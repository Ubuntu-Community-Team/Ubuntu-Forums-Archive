---
title: "How to list available network locations in system “Places” dialog?"
date: 2013-08-22
forum: General Help
---

### Post by dajare on 2013-08-22
Can someone help out with how to get Windows Share drives, visible  and browsable as bookmarks in Nautilus, into the system's "Places"  listing/dialog used by browsers when downloading files (for example)?


  In this screenshot, the grey column on the left is Nautilus (notice  the Bookmarks), and the "Save File" dialog on the right is a browser  download asking for location. I *cannot* navigate from that dialog to the bookmarked Windows network drives. The "goal" is to get the bookmarks of the M: and U: form in Nautilus into the "Places" options in the dialog on the right:

[IMG]http://i.imgur.com/ow4hEoa.jpg[/IMG]


I know this has been asked in different ways, eliciting different answers. Here on the Ubuntu forums, I've read through [fixing Windows Share browsing]("http://ubuntuforums.org/showthread.php?t=1169149") and [mounting Samba shares with utf-8]("http://ubuntuforums.org/showthread.php?t=288534"). On AskUbuntu, I've looked at [using SMBNetFS]("http://askubuntu.com/a/35724/38585"), or simply [browsing to ~/.gvfs]("http://askubuntu.com/a/29501/38585"), neither of which work for me. 


  FWIW, my network location has this form: smb://drivename.uni.ac.uk/school/HOME/username


  A clear, all-steps-and-info-required tutorial would be wonderful! I'm using Ubuntu 13.04. Thanks!

---

### Post by dajare on 2013-09-05
Is this really impossible? Is there *any* advice out there for this problem? On this same machine, running Win7 in Virtualbox, I can save to any drive available on the system. It's a genuine frustration that the Ubuntu "system" dialog doesn't seem to be able to find the network drive(s).

Any help would still be appreciated - thanks!

---

### Post by zazy on 2013-09-23
I agree with you all: this is a real PITA! Even if there is a workaround, this kind of leaks is one of the reason linux is hated from not-so-skilled users.

I use this workaround if anyone interested in:

1. Use Nautilus to navigate to the share and mount it (or use the mount command)
2. when you want to write/read a file from the share, simply go to /run/user/<username>/gvfs and there you'll found every shares mounted by the user. (Please replace the <username> with actual user login)

To avoid to navigate to /run/user/<username>/gvfs every time, I symbolic linked the directory with ln -s /run/user/<username>/gvfs ~/gvfs

Hope this help.

P.S.: Of course you can go to the /run/user/<username>/gvfs folder and press CTRL+D to add it to the bookmarks too!

---

### Post by dajare on 2013-09-24
> **zazy said:**
> Hope this help.

Yes, it helps *enormously*! Many thanks! This is the first bit of solid help I've had with this problem, and I've been asking in various places (nicely, I hope!) for a long time!

Can you further tweak this solution? My "share" in /gvfs has this form:

```
smb-share:server=machine.unit.uni.ac.uk,share=school
```

The directories I'm chiefly interested in are several levels down the "school" branch. Is there any way to get the "share" to point to the first meaningful directory? I tried just changing the "file name" in /gvfs, but it doesn't accept slashes.

Meanwhile, your help constitutes real progress for me. Thanks again!

---

### Post by zazy on 2013-09-26
Many thanks for your appreciation, Dajare ;)

Any app using the open/save dialogs have to explicitly enable network shares to be able to see networked bookmarks. To avoid all the problems related to networks, many apps disable this feature.
Worst: if you try to add a local mounted network share, Nautilus will convert it to an smb link.

Don't worry, I have a little trick for you but it's a little bit "ugly". Just to fix ideas I will use your [COLOR=#000000]*smb://drivename.uni.ac.uk/school/HOME/username* share.[/COLOR]

1. Mount smb://drivename.uni.ac.uk/school share in your preferred way
2. open a terminal window and give:
```
ln -s /run/user/<your-local-username>/school/HOME/username/anyotherfolder/orwhereveryouwanttobookmarkaslocal ~/mysharename
```
this will create a symbolic link in your home directory that will point to your deep path in the smb share. The symbolic link will be called mysharename. You can give it any name you like and put it in a subdirectory of your home directory if you want
3. start gEdit and open the file ~/.config/gtk-3.0/bookmarks
4. add this line wherever you want (the sorting order will be preserved - in some way - from Nautilus):
```
FILE:///home/<your-local-username>/mysharename Your preferred name here
```
5. Save the file

At this point in the Nautilus left panel the entry "Your preferred name here" will be shown and the same entry will be shown in the save/open dialogs.

Please note that if the share is not mounted when you try to save/open a file from a "not-network-enabled" app, it will not be mounted. You need to do it with Nautilus or in any other way by yourself.

Let me know if you need further details and sorry for my english... it's far from being perfect ^_^

---

### Post by dajare on 2013-09-26
Hi Zazy - thanks for the further help and interest. Your English is doing very nicely! :)

> **zazy said:**
> 
2. open a terminal window and give:
```
ln -s /run/user/<your-local-username>/school/HOME/username/anyotherfolder/orwhereveryouwanttobookmarkaslocal ~/mysharename
```
this will create a symbolic link in your home directory that will point to your deep path in the smb share.


Unfortunately, I can't make your trick work. I thought it might be because "/gvfs" is left out of the path you suggest, but I have tried quite a few variations, and none work. :-k 

If you have any ideas, that would be great - otherwise, what you have provided already above (and it is working very well for me) is the essential bit. I'm now also auto-mounting the share at startup, so everything is very slick now.

Thanks again!

---

### Post by zazy on 2013-09-26
D'oh! You're right, ln command in step 2 is completely wrong, sorry. 

It should be:
```
 ln -s /run/user/<your-local-username>/gvfs/smb-share\:server\=machine.unit.uni.ac.uk\,share\=school/HOME/username/anyfolder ~/mysharename
```
I suggest you to use the TAB key to obtain the correct full path.

Please note that if ~/mysharename already exist then the ln -s command will fail. So you have to delete it if you want to create it again.

---

### Post by bart2pub on 2013-12-07
Hi,

I 'solved' this not so nice flaw with gvfs and samba in a similar way. I just wanted to add some comment to clarify, and then ask some additional questions.

Location of the target for the symbolic link:
  Ubuntu <= 12.03           :   ~/.gvfs/
  Ubuntu 12.10 and 13.04  :   /run/user/<your-local-username>/gvfs/
  Ubuntu 13.10                :   /run/user/1000/gvfs/

When you create the symbolic link with the ln -s command, special characters like :, = and , have to be escaped with the \ character (as you can see in the code in comment #7)

The developers of gvfs moved the target out of the home directory (~) probably because if some application (like backup or search) would crawl the home directory, it could also start crawling the external server, which would take time and encumber the server. So I created my symbolic link not in the home directory but in the directory /media/<MyNAS>.

Now the questions:
- Which would be the best ownership and permissions for my directory <MyNAS> ?  (now in Ubuntu 12.10 owner is root and permissions drwxr-xr-x)
- Which would be the best ownership and permissions for the symbolic link ?  (now owner is <user> and permissions drwx------)
- Is there a way to trap the event when you click the symbolic link and there is no connection yet ?  This could be used to launch a window to fill in credentials (as when in Nautillus/Thunar you would browse the network) and then connect ...

I hope some day rather soon it will be possible for most applications to work with files on networks in an easy way. Having paths that change all the time aren't helping in this. Symlinks can resolve that (you can create your own structure independent from what's behind it). It would be nice if authentication also could be on the fly then ...

---

