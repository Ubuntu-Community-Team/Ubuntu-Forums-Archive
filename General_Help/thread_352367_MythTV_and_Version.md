---
title: "MythTV and Version"
date: 2007-02-03
forum: General Help
---

### Post by reclusivemonkey on 2007-02-03
Hi everyone,

Not really sure whether this should go in the media section, but it has a little to do with repos as well, so I'll stick it here for now.

I have mythtv-0.20  installed on Slackware 10.2 in the lounge. It works great :-) I would like to be able to watch mythtv from my desktop in another room. I configured mythtv on the Slackware box to do this, and then installed myth-frontend on my Edgy desktop. It all works fine, except when I try to connect I get the error message;

"The server uses network protocol version 30, but this client only understands version 31. Make sure you are running compatible versions of the backend and frontend."

Now ideally I want to update the Slackware mythtv box to Ubuntu, but for the moment it would be great if I could find a *slightly* older version of a mythfrontend deb that will work with my mythtv-0.20. Does anyone know where I can find one? Looking in synaptic, there is only one version for mythfrontend and I've googled around with not much look. TIA.

---

### Post by ximok on 2007-02-21
You and I are in the same boat.

Considering you are familiar with slackware, you can try following these installation instructions.

[http://www.mythtv.org/wiki/index.php/Ubuntu_Edgy_Installation](http://www.mythtv.org/wiki/index.php/Ubuntu_Edgy_Installation)

in a nutshell, download the myth-.20 source, you probably still have it from your slackware install

You can skip adding the user.

sudo apt-get build-dep mythtv
sudo apt-get install libqt3-mt-mysql

edit the ld.so.conf file (add /usr/local/lib to it)

I used this for my configuration line instead:
./configure --prefix=/usr --disable-backend

qmake mythtv.pro
make

and if all goes well...

make install

then, just run mythfrontend and configure it for your master server.

if all goes well, you should be right where you want to be.


I'm going to go do this right now (waiting for the compile to finish) and I'll let you know how I fair.

---

### Post by reclusivemonkey on 2007-02-22
Thanks, but I installed Xubuntu the weekend before and everything went fine.

---

### Post by ximok on 2007-03-05
LOL, well, I guess that solves the problem.

Sorry, I should have told you that the installation went well.

Out of curiosity, what filesystem are you using to store your recordings? 

I'm using XFS and it's working pretty good.

---

### Post by superm1 on 2007-03-06
> **reclusivemonkey said:**
> Hi everyone,

Not really sure whether this should go in the media section, but it has a little to do with repos as well, so I'll stick it here for now.

I have mythtv-0.20  installed on Slackware 10.2 in the lounge. It works great :-) I would like to be able to watch mythtv from my desktop in another room. I configured mythtv on the Slackware box to do this, and then installed myth-frontend on my Edgy desktop. It all works fine, except when I try to connect I get the error message;

"The server uses network protocol version 30, but this client only understands version 31. Make sure you are running compatible versions of the backend and frontend."

Now ideally I want to update the Slackware mythtv box to Ubuntu, but for the moment it would be great if I could find a *slightly* older version of a mythfrontend deb that will work with my mythtv-0.20. Does anyone know where I can find one? Looking in synaptic, there is only one version for mythfrontend and I've googled around with not much look. TIA.
Your better bet is to upgrade the slackware box to mythtv-0.20-fixes which includes the protocol change.  0.20-fixes has lots of stability related fixes anyhow :)

---

