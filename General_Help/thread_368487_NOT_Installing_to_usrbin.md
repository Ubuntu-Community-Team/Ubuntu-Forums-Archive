---
title: "NOT Installing to /usr/bin"
date: 2007-02-23
forum: General Help
---

### Post by lots on 2007-02-23
I'm setting up a server, and would like to install texlive into its usual spot in /usr. However I do not want the executables to be in /usr/bin. For this I want to install them to a separate folder in /usr/ that is not attached to any particular default path for ubuntu executables. This way I can share out texlive's folder in /usr/ and share out its executables (on their own) via NFS to the client systems. I prefer not to install texlive on all the machines in this network, as it will be much easier to maintain ONE installation of texlive rather than 20 :) Also, any fixes that occur, or extra packages that get added as time goes by, will be global for all users (as we use many custom packages that do not exist outside the department, and thus, not in the repositories).

Anything special I can pass to apt-get to have it install in this manner? I'm not an experienced user with apt-get :P I browsed a bit around the apt-get man page but wasn't really finding anything useful..

Alternatively, I could move these packages manually, but tex installs so many executabes, that finding out what the list of files in bin is would be helpful for this method :)

One more solution would be to use texlive's configuration script, but I am not sure this comes with the installation. Correct me if I'm wrong though :) I do know it comes on the CDs if you manually install ...

Anyway thanks for the feed back..

---

### Post by lots on 2007-02-23
*bump*

It fell off the first page :P

---

### Post by TheWizzard on 2007-02-23
most apps you install go to /usr/bin
if texlive doesn't go there, you can build it from source with parameters set to put it in /usr

---

### Post by lots on 2007-02-23
Well the point is I don't want it to go to /usr/bin :) I want to isolate its executables so I can share them to the other systems, without conflicting the /usr/bin directory on the clients.

I'll check the build from source... I assume > apt-get -b install texlive-full Is what I'm after?

Thanks for the help :)

---

### Post by TheWizzard on 2007-02-23
> **lots said:**
> Well the point is I don't want it to go to /usr/bin :) I want to isolate its executables so I can share them to the other systems, without conflicting the /usr/bin directory on the clients.

I'll check the build from source... I assume  Is what I'm after?

Thanks for the help :)

i'm not sure this is a wise practice. i don't think it'll work properly. 
if you want to save yourself work, there are better ways. e.g. with using local repo's. 

what's the problem with installing the app?

---

### Post by lots on 2007-02-23
There is no problem installing the app. normally, but I don't want a normal installation :)

I want to install texlive in something like /usr/texlive or /usr/local/texlive (something similar anyway). When texlive installs it installs a bunch of executable files to /usr/bin (or should, I have not done it yet). I do not want this, as I am planning to share texlive (and its binaries) via NFS to the other clients in the network.

The point is to have ONE texlive installation across the entire setup (server and the 20 some odd clients). This way I only have to maintain ONE installation rather than 20. And since we have a few custom tex styles we use constantly, that don't exist out on repositories or anything (since they're in house), it should simply the task of keeping the tex installation up to date. The packages used and developed in house also get revised fairly regularly.

Texlive's usual install path is fine. I'm really only concerned with the default install directory of the executable bits (tex, latex, pdftex, etc) I'd prefer these to be in thier own folder..

It should work fine so long as all the paths and texlive configuration files know where everything is. Which is fine and relativly easy to do, and I'll only need to do it once since I'll ghost the rest of the machines anyway.

---

