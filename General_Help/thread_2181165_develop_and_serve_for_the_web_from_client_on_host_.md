---
title: "develop and serve for the web from client on host files"
date: 2013-10-16
forum: General Help
---

### Post by twinturbotom on 2013-10-16
**Objective:**
Streamline web development on a machine with multiple operating systems and environments (some of which are better than others)[B]. 

Background:[/B]
I have a windows machine constantly crunching numbers on windows only engineering software.  Everything else I use a computer for is on an a linux desktop VM or an ubuntu server that is always on.  I'm setting this machine up for web development (which I used to do predominately from a linux laptop) and am looking for an effective means to develop without redundantly storing files and installing software.  Ultimately I intend on having my server, serve private websites internal to my network.  This means it will have rvm, ruby, git, passenger, nginx, and an assortment of other applications.  I began setting up my linux desktop to develop and found my self ready to repeat software installations and configurations.  Once that's done I was considering a 3rd round, on my windows machine, and that's when I stopped; I loathe using windows for web development and am thinking that I can avoid a 3rd round of configuration if I do things properly, maybe even a second round!

**My Proposed Solution:**
[LIST=1]
[*]Install the necessities on my server.
[*]Mount (server and linux desktop) a location on the windows host where all my source code will reside.
[*]Manage source control and physically serving through ssh on server.
[*]Edit files (code, images, files,...etc.) on any of the 3 machines with applications from any machine... Sublime text, GIMP, Inkscapte,...etc.
[/LIST]

[B]Concerns:
[/B]
[LIST=1]
[*]Files are physically accessible from my windows machine without having to boot any VM's.I feel like this is an opportunity to introduce the potential for corruption.  Git, ruby,...etc. will all be on a server that may not be active while editing files.  Not to mention meta-data and other temporary files are handled differently between OS programs.
[*]Challenging for my windows or linux desktop to see server's localhost?  I'm sure this can be worked out considering it's setup with a bridged adapter and easily communicates with my network.
[*]Managing host files from a VM and issue?  I move things around and edit quite a bit but not git or programing code
[*]My production server housing development work?  I like pushing things from my development machine to a production server...  What I'm proposing going to be okay?
[/LIST]
[B]
Direct Questions:[/B]
[LIST=1]
[*]Are my concerns valid?
[*]Should I set this machine up as I've proposed?
[*]Any ideas on how to set this machine up without having to duplicate several installations, configurations, and not be constrained by a single OS?
[/LIST]

[B]Most Importantly:
[/B]Thank you for your mind share and consideration!  I look forward to any guidance.  Thank you!

---

### Post by TheFu on 2013-10-16
Pick 1 machine to perform RoR development and use that.  Edit on that machine, run the code on that machine and ci/co of git on that machine.  Backup that machine religiously too.

The other machines become remote access terminals either iwth a remote desktop or ssh.

I've been developing software like this for 20+ yrs - including RoR, Perl, C/C++.  Over all that time, a few things have changed, but not the ideas around development. Especially for web development, there isn't any need to have stuff local.

When it comes time to push your code to production, let your Gemfile and bundler handle dependencies - use git for your deployment.

Doing RoR development on Windows is too painful to consider for many, many, many reasons. It just isn't worth the hassles.

---

### Post by twinturbotom on 2013-10-17
Thank you for your advice here.  I completely agree with you to not consider the windows machine as a development platform.  That being said, I'm still hesitant to save this data in my VM's ".vdi".  I'm thinking my ubuntu VM will be setup to develop there but the files will reside on my windows host.  This way if I need to quickly access something I can.  The server will be setup with what is needed to actually serve the applications.

This stuff will most likely be local only as it's for internal use.  I don't want to fill up my git account with a bunch of private repos that are only meant for serving on my local network.

Thanks!

---

### Post by SeijiSensei on 2013-10-17
> **twinturbotom said:**
> I'm still hesitant to save this data in my VM's ".vdi".  I'm thinking my ubuntu VM will be setup to develop there but the files will reside on my windows host.

I never store data in VM images.  Everything I need resides on my network server running CentOS and accessible via NFS or Samba.  Another alternative would be to store the data on the machine hosting the VMs and use a function like "shared folders" in VirtualBox to access them.

---

### Post by TheFu on 2013-10-17
> **twinturbotom said:**
> Thank you for your advice here.  I completely agree with you to not consider the windows machine as a development platform.  That being said, I'm still hesitant to save this data in my VM's ".vdi".  I'm thinking my ubuntu VM will be setup to develop there but the files will reside on my windows host.  This way if I need to quickly access something I can.  The server will be setup with what is needed to actually serve the applications.

This stuff will most likely be local only as it's for internal use.  I don't want to fill up my git account with a bunch of private repos that are only meant for serving on my local network.

Thanks!

Huh?  What does a "git account" have to do with anything?  You can easily setup a local master git repo. Takes about 10 minutes, including the reading needed - the free ProGit ebook explains.  If you don't want to store files on github, use a different service that allows non-public projects.  bitbucket?  I don't know, since we only use an internal git repo for all our projects. ssh access is basically all that is needed. Nothing fancy that I can recall, purely ssh+keys.

Don't keep files on Windows. The file permissions will screw you.  If you like, you could create a bonehead script that mirrors the files to your Windows area, if you like, but using a central git repo would be easier and part of your existing workflow, correct?

How many physical systems do you have?  Isn't 1 a linux "server" that is always on and where you backup this stuff?

I never keep important files on Windows.  A VM is better because I can back it up 100% trivially, migrate it to a different VM host and restore - then I'm 100% productive should the host machine fail.  Any machine that can run VirtualBox is my savor. I've been overseas when a laptop failed. Thankfully, I'd exported the VM just before heading out on the trip. Bought a new laptop for $500, downloaded the VM overnight and I was back up running the next day. All my settings, programs, data 100% perfect.  Daily data backups mean I don't have huge VM files everywhere.  Just one from the last few months, then restoring the changed data is trivial.  Linux is always a better host for data than Windows, IMHO.

---

### Post by twinturbotom on 2013-10-17
I think I get it... Thank you for your insight.
I'll set my linux server as a git server and then i can develop from any of my machines.  Only issue is that there are times when my main linux desktop VM is not on and I may need to change a few bits of code, which I can do from windows easily without having ROR installed.
Similar to Sensai I do typically avoid storing things in a .vdi, but TheFu may have changed my opinion on that.  Seems like a nice way to make a machine portable (if the new host has the resources to run my VM).

Thank you for the direction.

---

### Post by TheFu on 2013-10-18
How many physical machines do you have and what types are they - server, laptop, netbook, desktop?
If you are in the USA, you can get a free "tiny" VM from Amazon for a year. That would certainly be enough for a git repo.

---

### Post by twinturbotom on 2013-10-18
I have 3 laptops (Windows (Windows - 12GB RAM, Ubuntu - main machine - 2GB RAM, Mac OSX - the first two are used extensively) and 1 physical machine running up to 4 VM's (1 ubuntu server, 2 windows 7, 1 ubuntu desktop).  The server is always on and gets used for various things.  The windows machines are basically crunching engineering data all day and the ubuntu desktop VM is my preferred "machine" to use.  I'll look into the amazon angle.

I guess I'll start with hosting a local git server that enables me to develop from any of the machines I have (as long as I can access my server).  I'll try using my .vdi for my main ubuntu VM that I'll also develop with.  

Thank your the discussion.

---

### Post by TheFu on 2013-10-18
The main things I'd like to stress are:

* backups, backups, backups. If the data isn't in 3 places, then you DO NOT HAVE a backup.

* Store important data on a UNIX-based file system. It can act like Windows/NTFS if you need that with samba. The opposite is NOT true. No NTFS share can support UNIX-style permissions.  I've seen editors fail using VirtualBox file sharing from a Windows-HostOS and when trying to edit using normal Win-folder shares. The file locking isn't the same.

With git, you'll have the data on different physical HDDs, right?  3 copies on the same physical HDD host and 2 client-OSes doesn't count. If only 1 HDD is installed in that machine, that is 1 copy.  HDDs fail everyday. ALL of them will fail, eventually and it is never convenient when it happens.  Heck, I rotate HDDs from main, to backup, to giveaway status.  I've had HDDs fail in each type of use.

---

