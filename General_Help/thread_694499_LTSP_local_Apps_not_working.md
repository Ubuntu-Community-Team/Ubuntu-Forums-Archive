---
title: "LTSP local Apps not working"
date: 2008-02-12
forum: General Help
---

### Post by bvsantos on 2008-02-12
Hi all.

I've installed Ubuntu 7.10 and, following the quick guides, i've installed LTSP. 

Everytime i want to install an app in the LTSP environment, i do a chroot for the LTSP directory.

Take for example, firefox. In the chroot, i install firefox, and do an ltsp-updat-image.

Fire up a thin client, but no firefox.. :-k
I only have a firefox in the thin client when i install it on the server..

am i doing something wrong or is this the default behavior ? Where is the local apps theory ?

Cheers,

Bruno

---

### Post by Deadpan110 on 2008-06-01
This seems to still be a 'work in progress' by the Ubuntu LTSP developers - and rightly so.

Following [http://www.ltsp.org/twiki/bin/view/Ltsp/LocalApps](http://www.ltsp.org/twiki/bin/view/Ltsp/LocalApps) and [http://www.ltsp.org/twiki/bin/view/Ltsp/LocalAppFirefox](http://www.ltsp.org/twiki/bin/view/Ltsp/LocalAppFirefox) is quite complex but can give a brief understanding of requirements needed for this to work.

I would imagine to come up with a nice and easy Ubuntu package install to enable all the components needed could be a nightmare.

But anyways, you have installed Firefox in your LTSP root image - and if you are not afraid of playing around, you can get it working by cheating...
(**Please note**... _Do Not_ Use my methods for production servers - this is just an example to show you it works)

[LIST]
[*]Make sure you have installed ssh into your LTSP root image:
```
sudo chroot /opt/ltsp/i386/
apt-get install ssh
exit
```


[*]You need to authenticate the user on the local client - We should use some kind of network authentication here (LDAP/NIS) and also set up some method of setting up ssh authentication keys - but for the purpose of this exercise... we cheat:
[LIST]
[*]open /etc/passwd /etc/group and /etc/shadow on the server and copy the user you want into the corresponding files within the LTSP client root
[*]create the users home directory within the LTSP client root and chown it accordingly
[/LIST]
```
# Our example user is called 'foobar' within group 'foobar'

# Entry from /etc/passwd to be copied into /opt/ltsp/i386/etc/passwd
foobar:x:1000:1000:foobar,,,:/home/foobar:/bin/bash

# Entry from /etc/group to be copied into /opt/ltsp/i386/etc/group
foobar:x:1000:

# Entry from /etc/shadow to be copied into /opt/ltsp/i386/etc/shadow
foobar:$1$xSOMEENCRYPTEDKEYSHOULDBEHEREx:14019:0:99999:7:::

# Now we create the users home directory
sudo mkdir /opt/ltsp/i386/home/foobar
sudo chown foobar:foobar /opt/ltsp/i386/home/foobar

# Don't forget to update the LTSP client image
sudo ltsp-update-image
```
Imagine having to do this for EVERY user you add to your terminal clients - not forgetting that if you add more later, you will have to run ltsp-update-image and reboot clients to see the changes and it soon becomes apparent why network authentication is needed!

[*]Boot up a client and log in as the example user 'foobar' then type the following into the Gnome terminal emulator to see if it works:
```
rsh ${LTSP_CLIENT} DISPLAY=":6.0" /usr/bin/firefox -display :6.0
```
This is where we find out why SSH keys are needed, you should get a dialog box with 'Yes or No' - type 'yes' as this is the client asking you if you want to accept its public keys. Then you will get another dialog box asking for your (foobar's) password.

If all is correct, you should now have Firefox running as a LTSP Local App on your desktop.
[/LIST]

After playing around using this method to test what exactly is going on, it soon becomes apparent that not only network authentication and ssh keys are needed (for password less operation), but we are missing the users home directory also.

(Firefox will save files onto the Local LTSP client root - along with any settings/cache files which will be lost upon reboot and you will not be able to upload things like photos from your Desktop onto your favorite blog/social networking/website as they are not available to the app.)

The LTSP Server /home directory will need to be exported with NFS or other means in order for things to work correctly.

*I have been playing with the idea of using NBD and OCFS2 (Oracle Cluster File System) on my LTSP setup*

I hope this helps give some insight into getting Local Apps working :razz:

---

### Post by Deadpan110 on 2008-06-07
I have done a lil more to get Local Apps working on my LTSP client...

I now use NIS which is set up on the server and within the chroot using:
[https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)
(I have used it before but prefer LDAP, but for the sake of a quick fix - following that howto is nice and easy)

I am also using NFS :( which can be set up using this howto:
[https://help.ubuntu.com/community/SettingUpNFSHowTo#head-ac7dfba15ed58c9d4cdb3417a2ab2f2433d444f0](https://help.ubuntu.com/community/SettingUpNFSHowTo#head-ac7dfba15ed58c9d4cdb3417a2ab2f2433d444f0)
(Yups NFS is not the best thing to use - even I dunt like it - but as long as ya clients and ya server is set up securely and you want a quick fix - then jump right into the Installation and Configuration section and also  add autofs to your chroot)

I then wrote a script on the terminal server to start apps on the client... this includes a very simple server key check/install ...again... its a quick fix... ima not gunna paste the whole lot here as I get ashamed of very messy code (I write messy code by default - but my script is extremely bad)

If Ubuntu LTSP Devs have not got their nice n easy Local Apps working within a few months or so, then maybe I can be persuaded to slap the lot into a SVN repository somewhere n let ppl have r/w access - but to be honest... I would rather wait fer a non NFS Ubuntu LTSP Local App solution than use my scripts!

Once you have NFS, NIS and autofs working on your client (test by logging into your client as a user and see if their home dir is there), you are ready to plop together some script on the server... mine is called /opt/ltsp/local-apps/run-local.sh and it basically checks if running on the server or client, checks or installs keys then runs the app you want from the client: /opt/ltsp/local-apps/run-local.sh /usr/bin/firefox

So anyways... to do things manually, open up Gnome termimal emulator on the client and do the following:

```
# You only need to create and import this key to authorized_keys once
ssh-keygen -N '' -t dsa -f ~/.ssh/id_dsa
cat ~/.ssh/id_dsa.pub >> ~/.ssh/authorized_keys
# Replace firefox with what ever app you have in your client root
rsh -o StrictHostKeyChecking=no ${LTSP_CLIENT} DISPLAY=":6.0" /usr/bin/firefox
```

Mine has a few env vars in the last part just to make sure some things work... but the above should get things working.

So far, I have Local Apps of Firefox 3 (with working flash), Xchat, Google Earth, Digikam and Skype (altho no got sound working quite yet)... I plan to add OpenOffice, Amarok and maybe Vlc (or some media player).

If none of my previous postings seem to work, then maybe /var/lib/tftpboot/ltsp/i386/lts.conf needs a quick double check:

```
[default]
SOUND = True
LOCALDEV = True
LOCAL_STORAGE  =  True

# Set to my server, just in case
LDM_SERVER = "192.168.1.1"

# Setting LDM_DIRECTX causes things to fail
# LDM_DIRECTX = True

LOCAL_APPS = True

# Setting USE_LOCAL_SWAP is important if you want to use things like GoogleEarth...
# Im not sure, but as long as a clients drive has a swap partition that is actually
# marked as type 82 within cfdisk (Linux swap / Solaris), this works nice
USE_LOCAL_SWAP = True
```

Some of the above I am not entirely sure if I have bypassed with some of my methods... as I stated above... its all a quick fix and without myself knowing the ins and outs of LTSP as much as I would like... perhaps some Ubuntu LTSP devs will read this and shed some more light on the subject...

In the mean time... have fun playing with your local apps!

---

