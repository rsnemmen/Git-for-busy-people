Git basics
===============

This is quick tutorial on how to use `git`. The idea is to grasp the basic concepts needed to download and perhaps contribute to an existing git repository (let's say, [github](https://github.com) or [bitbucket](https://bitbucket.org)). 

# Setup your identity for the first time

You want to setup your identity (name and e-mail) for the future. You only need to do this once in each machine where you work:

```
git config user.name "Your Name"
git config user.email "me@example.com"
```

# Download files for the first time

To create a local copy ("clone") of the project in your machine:

    git clone https://user@bitbucket.org/user/projectrepo.git
 
where you replace the username and project name in the command above with the address from github/bitbucket or the one your collaborator gave you. This will create a folder called `projectrepo`.

Let's see the history of "saved snapshots" (commits) of the project so far. Change to the project directory and type:

    git log


# Changing things, "saving the game"

Now you decide to edit some file(s). If you need to add a file which is not in the project, you can issue

```
git add newfile
```

To inspect what you changed with respect to the last saved state of the project:

```
git diff
```

Once you are done with your editing, you want to save the state  of the project. I like to think of this using an analogy with videogames: you save your game and can easily go back in time, if things go wrong later. In the git world, saving the game is called *commit*.

Suppose you changed a source code file in the repository directory. To save the state of the project, you could use the following command:

```
git commit -am "added the discussion section and figure with time variability"
```

with a short description of what you changed. 

If you want to describe things in more details, just issue `git commit -a`. This will open a text editor which will prompt you for a description of what changed. It is standard practice to begin the commit message with a single short (less than 50 character) line summarizing the change, followed by a blank line and then a more thorough description. 

By the way, when writing a longer commit message, the default git text editor is VI. I particularly do not like this editor and instead prefer to use nano. You can change the text editor used by git with this command:

    git config --global core.editor nano


# Uploading changes to the cloud

When you commit, the changes are only saved locally in your machine. To upload the changes to the cloud such that it is accessible to collaborators, first commit your code then issue

```
git push
```

*Nothing is uploaded to the project until you both commit and push*. 

If the repo is owned by you, your changes should be immediately available in the cloud (github, bitbucket or wherever you keep your repo). If not, then you need to follow the procedure of [submitting a pull request](https://opensource.guide/how-to-contribute/#opening-a-pull-request). 

# Downloading updates on the project

After a while, your collaborators probably did some work and changed things. To update the state of the project with the latest changes: 

```
git pull
```

This will download the files from the server and update the project on your machine.


# Creating alternate, exploratory, "savegames"

This concept is a little more advanced. Suppose you have some awesome idea which is tricky and may put the project at risk and/or introduce bugs. Instead of having one single save state which is continuosly evolving and updated by everybody (in the git language, the *master branch*), you can create a parallel save state which will have a copy of the project and keep the stable version of the project safe aside. Let's call this alternate save state "explore":

```
git checkout -b explore
```

The command above creates a *branch* (the alternate save state) called explore and switches to the new branch. Now everything you do is saved in the explore branch. 

When you are done with your awesome exploratory idea and want to go back to the "stable" branch, first *commit* then

```
git checkout master
```

Once you find out that your exploration ended up improving the project and sorted out all bugs, you can merge the stable and the exploratory branches. First commit, then switch back to the master branch as in the command above, and type

```
git merge explore
```

<!---
If you decide to upload the new exploratory branch to the remote server, you can do a push command
-->

# More

I skipped here some concepts, such as creating a local repository in your machine, uploading your new local repo to a remote server, fixing a wrong commit message, defining workflows and many other things, for the sake of brevity.

You can find useful material in the following websites:

* [Bitbucket 101](https://confluence.atlassian.com/display/BITBUCKET/Bitbucket+101) and their [Git tutorials](https://www.atlassian.com/git)
* More in depth tutorial: [Git Magic](http://www-cs-students.stanford.edu/~blynn/gitmagic/)
* [Super quick Git guide](https://wiki.archlinux.org/index.php/Super_Quick_Git_Guide) at archlinux
* [A simple guite to Git](http://rogerdudler.github.io/git-guide/) (check out their cheatsheet)
* [One cool cheatsheet here](https://github.com/AlexZeitler/gitcheatsheet/blob/master/gitcheatsheet.pdf) and [here](http://www.git-tower.com/blog/git-cheat-sheet/)

- - - 

[Visit the author's web page](https://rodrigonemmen.com) and/or follow him on twitter ([@nemmen](https://twitter.com/nemmen)).