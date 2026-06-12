---
title: "Help requested with Git + SSH setup"
date: 2017-03-25
forum: General Help
---

### Post by Victor Rafael Rivarola on 2017-03-25
I do not know how to ask for this. Everything I find on the net is about getting your SSH key to log in automatically in GitHub and the like. This is not what I need to do.

I have (yes, have) my own server (yes, my own) on a remote location. I want to set it up so I can administer a software I am currently working on via Git/SSH.

I have it currently set up with the Git repository working flawlessly, but I am mounting the Git share as a share with SSHFS, and then accessing it as if it was on a local disk with my Ubuntu notebook. 

This neutralizes many of Git team work features, however it means I have the working repository correctly set up, with the SSH keys, and everything. Plus I have my system automatically set up to acquire my SSH passphrase and mount the SSHFS share automatically and correctly.

How do I go about changing my current setup to the normal Git setup for SSH access?

---

### Post by dragonfly41 on 2017-03-25
This is more of an intuitive answer to your question since I'm not quite sure if it meets your needs. But it touches on some automation I'm grappling with.

You write that you want to control your &#8220;own server&#8221; via SSH.

In my case I'm experimenting with rapidly setting up applications on some cloud based servers.   After I delete a server instance I want to rapidly bring the fresh VM instance up to date and I don't want to use raw snapshots.   So there are many actions to take in sequence after creating a new VM instance.

Recently I found reference to Fabric.

[https://gist.github.com/DavidWittman/1886632](https://gist.github.com/DavidWittman/1886632)


[http://docs.fabfile.org/en/1.13/usage/ssh.html](http://docs.fabfile.org/en/1.13/usage/ssh.html)


One attractive feature of Fabric is the ability to run on a local desktop a batch of fabfile scripts which are executed in the remote server.

This opened my eyes to different ways of setting up remote servers, from a local desktop.

For example I'm now building a local repo of &#8220;fabfiles&#8221; to install packages on a remote headless Ubuntu 16.04.   All my fabfiles are in a fabfile directory (see fabfile discovery and namespaces).  Inside the fabfiles folder you need a python file ___init__.py to discover all local fabfiles which are just small snippets of python code.   There could be a single fabfile but I'm breaking up the actions into a library of many fabfiles, even in sub folders.

The previous workflow I was using was to upload bash scripts onto the remote server then run those scripts through an SSH console session.

Pay attention to Project Tools described here.

You can, for example, run a fabfile on your local desktop which runs a fabfile to push/pull content from github to/from remote server using rsync.

[http://docs.fabfile.org/en/1.13/api/contrib/project.html](http://docs.fabfile.org/en/1.13/api/contrib/project.html)

To summarise all your automation fabfiles are in your desktop repo.

So my guess is that using Fabric in your workflow might help.
But it is a guess.   I have not yet got to the point of integrating Fabric with github as a triangle - 

                  local desktop &#8596; github
                  local desktop &#8596; remote server
                  remote server &#8596; github

Here are threads I found referring to using Fabric with SSFH

[http://stackoverflow.com/questions/24317368/sshfs-mount-failing-using-fabric-run-command](http://stackoverflow.com/questions/24317368/sshfs-mount-failing-using-fabric-run-command)

[https://superuser.com/questions/139023/how-to-mount-remote-sshfs-via-intermediate-machine-tunneling](https://superuser.com/questions/139023/how-to-mount-remote-sshfs-via-intermediate-machine-tunneling)

...

And some threads referring to Fabric with github

[http://stackoverflow.com/questions/10226618/how-do-you-define-the-host-for-fabric-to-push-to-github-updated](http://stackoverflow.com/questions/10226618/how-do-you-define-the-host-for-fabric-to-push-to-github-updated)


[https://github.com/kracekumar/sachintweets/blob/master/fabfile.py](https://github.com/kracekumar/sachintweets/blob/master/fabfile.py)

...

However, I would not be surprised if some SSH experts add some alternative approaches.

---

### Post by TheFu on 2017-03-25
You don't need sshfs.
For each repo, setup normal workgroup management of the entire directory tree. That usually means putting the different userids (all need ssh) into the same unix group (ourgroup) (I would use **gpasswd**), making the top project directory /opt/git/OurSoftware and doing a **chgrp ourgroup /opt/git/OurSoftware** followed by a **chmod g+ws /opt/git/OurSoftware** so that all created sub directories are automatically forced to be 'ourgroup'.

This is a standard way for different users to work together on the same files on any Unix system.

There is a free PDF book called **ProGit**.  Setting a repo took me about 5 minutes and about 3 pgs of reading in that book. Google finds it easy.  Do a git push and set your origin to the repo, if you like.  After all, git is really just a social contract/agreement where to merge files.  

If you don't want to provide other users with direct access to the repo, then you can have them send you a pull request. If you have access to their git, you can merge their changes into your branch at will.  Use a new branch for each change authorization.  branching and merging is a way of life with git. Very powerful.

It has been a few years since I setup our git repo, but I don't think much more than that was needed.  The book made it really easy to setup.

And please secure your ssh connections.

---

### Post by Victor Rafael Rivarola on 2017-03-25
Thanks DrangonFly41!

Unfortunately, it does not solve my problem. 

You see, I am not dealing with multiple servers at this time, just one. Maybe multiple clients (in the future), but just one server. By the way, I said it was my own server to mean I have root access to it and I installed it.

Thanks to you TheFu!

I know SSHFS is not needed. It was just a simple way for me to quickly set it up and get it working so I could do some work while not understanding exactly how Git is supposed to work. I knew all the time that, by using it, I was nullifying some of the most important features of Git. 

I have already found the Pro Git book you mentioned me. I will read it in full and use the things it contains. Once again, thank you!

---

