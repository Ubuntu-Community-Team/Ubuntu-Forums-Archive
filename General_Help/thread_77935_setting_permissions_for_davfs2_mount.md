---
title: "setting permissions for davfs2 mount?"
date: 2005-10-17
forum: General Help
---

### Post by ivomans on 2005-10-17
I've installed & tried using the davfs2 package with Breezy. The idea is very nice: I'm now able to mount a dav-directory on my system. Unfortunately somehow the permissions are set to only read & write for root ("700"). 
Cann't find a way to make this available to normal users.

from /etc/fstab:
```
http://url-to-host/dav-dir/  /media/dav  davfs  user,noaskauth  0  0
``` 
and I added a line in /etc/davfs2/secrets with url, username, password.

I can see the mount is properly working with a [FONT=Courier New]sudo ls /media/dav [/FONT]
Anybody know a way to make this available for normal users?

Ivo.

---

### Post by pablo13 on 2005-10-17
Hi, I'm not sure if this will solve your problem ... I gess you can use the umask option on the fstab file. For example, I have the next line for mounting WinXP filesystem with 770 rights, "root" owner and "users" group 

/dev/hda1 /mnt/C  ntfs user,noauto,umask=007,uid=root,gid=users,iocharset=utf8  0       0

Hope this helps! Bye,
Pablo

---

### Post by ivomans on 2005-10-17
Pablo, Thanks for the suggestion, but unfortunately the options umask, uid, gid, etc. are not supported for davfs2. Trying to use one of these options results in an errormessage.

Ivo.

---

### Post by shadow on 2005-12-27
I wondered if you ever got this sorted out ivomans?

I've just hit exactly the same issue, chmodding or chowning doesn't work either since the operations aren't supported :/

---

### Post by ivomans on 2005-12-28
shadow,  Unfortunately not. 
I only found some people with same problem on forums from other distributions.

Ivo

---

### Post by shadow on 2005-12-28
Hmmm, that sucks :(

I thought I was on to something when I saw [http://cvs.sourceforge.net/viewcvs.py/*checkout*/dav/davfs2/README](http://cvs.sourceforge.net/viewcvs.py/*checkout*/dav/davfs2/README) on the section about 'MOUNTING' but even that doesn't work.

---

### Post by Ted_Smith on 2005-12-28
Is anyone able to respond to my last post (post 10 of page 1) - I think it's been forgotton due to it being at the end of the last page.

---

### Post by ivomans on 2005-12-28
[quote=Ted_Smith]Is anyone able to respond to my last post (post 10 of page 1) - I think it's been forgotton due to it being at the end of the last page.[/quote]
Ted, Looks like you got lost in wrong thread. There are only 7 posts in this thread so far.

---

### Post by Ted_Smith on 2005-12-28
Ooops, sorry - maybe webmaster can delete? My mistake.

---

### Post by shadow on 2005-12-28
ivomans, after a bit of research I've finally got it working pretty well.

Heres what I did to get it going:

> 
- Create a hidden directory '.davfs2' in your home directory

- Copy file 'secrets.template' from '/usr/local/share/davfs2' (or
  '/usr/share/davfs2' into directory '~/.davfs2'.

- Change its name to 'secrets' and file mode to 600.

- Edit a line in 'secrets' like
  [https://foo.bar/myfolder](https://foo.bar/myfolder)     myname    mypassword

- Ask root to make an entry in '/etc/fstab' like
  [https://foo.bar/myfolder](https://foo.bar/myfolder)   /media/dav   davfs   user,noauto   0   0


(The above is from [http://cvs.sourceforge.net/viewcvs.py/*checkout*/dav/davfs2/README](http://cvs.sourceforge.net/viewcvs.py/*checkout*/dav/davfs2/README))

- Add your username to the 'users' group (best way I found to do this was to use the ubuntu gui) System -> Administration –> Users and Groups then 'Groups' tab, double click 'users' and add your name from the left to the right.

[IMG]http://gav.brokentrain.net/upload/users.png[/IMG]

- Relogin-logout (Unsure if it's necessary though, but did it anyway.)

- Type:

```

sudo chmod 1774 /var/run/mount.davfs
sudo chown root:users /var/run/mount.davfs
mount /media/dav

```

..and it should now be mounted from your username.

Let me know if that helps,

Gavin.

---

### Post by ivomans on 2005-12-28
WORKING!  :):):)

With a few minor remarks to shadow's post:

The template file is found in /usr/share/doc/davfs2/examples/secrets.template, although you could also simply create a new ~/.davfs2/secrets file and just type the one line```
 [https://foo.bar/myfolder]("https://foo.bar/myfolder")     myname    mypassword
```  
Furthermore I needed to setuid two additional files:
```
sudo chmod 1774 /usr/lib/mount.davfs-2.6
sudo chmod 1774 /sbin/mount.davfs
``` 
Seems to work without a problem then. 
Whow, this is very interesting for filesharing between locations!

---

### Post by shadowman on 2006-01-14
Ok I don't feel so dumb now.  The irritating part for me is that I've used davfs for years with mandrake and suse and never had to jump through hoops like this.

Spoke too soon-still not working for me.  All that you have to do to mount is type: mount /home/john/whatever/your/mount/point/is?

---

### Post by nitrosx on 2006-02-01
I've read trough this tread and tried, but no luck.
Everytime I mount something with davfs, I get that root is the only one who can  read and write.

Any new idea??

Thanks

---

### Post by nitrosx on 2006-02-01
Hi everybody

It seems that I found the solution to our "little" issue.
Here are the instructions:

1) Uninstall davfs2
2) Reinstall davfs2 using Synaptic Package Manager (This way we start fresh)
3) cd /usr/share
4) sudo chmod u+s mount.davfs
5) cd /usr/lib
6) sudo chmod u+s mount.davfs-2.*
7) cd /var/run
8) chmod 775 mount-davfs
9) chown root:users mount-davfs
10) Make sure that your account is part of the group "users"

Be careful, because this way when you run mount.davfs, you'll run it with rut privileges. It can be dangerous!!!

To mount anything:
1) login as your self (no root)
2) mount.davfs <source> <dest-folder> -o rw
it will ask you to authenticate if that's the case, and... DONE!!!
That's it.

Let me know if it doesn't work
Ciao
MAX

---

### Post by cillian on 2006-02-05
I tried all the steps above (except for nitrosx's) and it didn't complain when I mounted it as a user but it didn't really mount anything i.e. when I tried 
$ls /mnt/webdav 
nothing came back. As root I could mount it no problems without any messing.

I installed it from source and I was up and running in no time. (Of course I do prefer to use packages but when you have to fiddle with them so much I feel like it's defeating the purpose, and I guess if the package was updated you'd have to fish out the solution again.)  Just in case anyone is a little wary of installing from source here's all it takes.

(if you've installed the davfs2 package you'll want to remove it first)
#apt-get remove davfs2

starting from scratch and step-by-step:
added my user to the users group as described and then
$sudo su
#apt-get install libneon24 libneon24-dev
#exit
$wget [http://prdownloads.sourceforge.net/dav/davfs2-0.2.7.tar.gz?use_mirror=surfnet](http://prdownloads.sourceforge.net/dav/davfs2-0.2.7.tar.gz?use_mirror=surfnet)
$tar xfvz davfs2-0.2.7.tar.gz
$cd davfs2-0.2.7
$./configure
$make
$sudo su
#make install
#chmod u+s /usr/local/sbin/mount.davfs
#mkdir /mnt/webdav
#gedit /etc/fstab
add the following:
[http://www.example.com/webdav/](http://www.example.com/webdav/)   /mnt/webdav   davfs   rw,user,noauto   0   0
#exit
$mount /mnt/webdav

---

### Post by nlvivar on 2007-04-12
have you checked out this thread?
[http://ubuntuforums.org/showthread.php?t=202761](http://ubuntuforums.org/showthread.php?t=202761)

---

### Post by flint_ on 2007-04-20
With the fstab entry containing these two options: users,noauto the following behavior may be expected.
The behavior is that  that the mounted filesystem inherits the permissions of the mount point, including uid, gid and rwx settings.  

If the mount point is permitted to root:root, a user will not be able to write to the filesystem
If the mount point is permitted to user:user, then the user will be able to write to the filesystem

Set the permissions on the mount point prior to mounting the filesystem to it.
note that files written in the file system by various users, members of a common group will retain their authors permissions unless specifically changed.

Is this correct?

---

### Post by ecor6633 on 2007-09-26
You have to things that you can do.

1. using fstab with "user,noauto" options so that the user who mounts the dav point is the owner of the folder.

with such a line :
```
http://mywebsite.com/davpoint    /mnt/mountpoint    davfs    noauto,user    0    0
```
I can mount my davpoint and it has my user as owner and group with 755 rights.

[I]To use that system i had to change /usr/sbin/mount.dafvs with setuid
```
sudo chmod u+s mount.davfs
```
[/I]
2. You can use mount command like this :
```
sudo mount -t davfs http://mywebsite.com/davpoint /mnt/mountpoint -o uid=myuser
```
but don't forget to use the options with -o and set the uid you want to use.

---

I prefered using /etc/fstab so that $HOME/.davfs2/secrets file is one file per user. When you use mount command in sudo it means you will temporarily become root and davfs search /root/.davfs2/sercrets and not $HOME...

---

