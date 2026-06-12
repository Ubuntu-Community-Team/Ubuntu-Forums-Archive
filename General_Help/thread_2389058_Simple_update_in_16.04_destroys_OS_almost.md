---
title: "Simple update in 16.04 destroys OS almost"
date: 2018-04-10
forum: General Help
---

### Post by ubuntubrian on 2018-04-10
Hello 
all and thanks in advance. This is a bit long but here's the story. I have been upgrading my OS since 10.04 rather than clean installs. I've worked through glitches and been very happy with the results. I run a lot of VM and 3rd party apps. This has helped me "learn" a lot but not enough. I ran a normal update and upgrade as prompted by Update Manager and was prompted to reboot, which I did. No splash screen but only being able to log into text mode. No X and startx only returned errors. I had posted here about this for some time and received no responses. 
We have a local Gnu/Linux group here of mostly admins and the sort that work at our labs and some are extremely proficient. After posting to our group one of them requested to meet and he'd look at my laptop and was sure he could work it out. Turned out to be more than he thought and he started an rsync backup while he worked from the command line and finally got a minimal xfce environ. to function. As he opened up to 6 xterms and literally typed faster than I could imagine and the commands I couldn't remotely keep up with. Nor did he have time then to explain much. He left the meeting for another with the rsync running and my battery dying and suggested that I sit the remote drive gently on the car seat with my laptop, get home, plug in and let the rsync complete. Well the USB cable jiggled loose and the process stopped so I plugged it back in and ran the rsync (he'd written a script for me to make it easy). I kept getting errors after the rsync ran and he suggested that I track each file down that caused the error and decide if it was needed, had the correct permissions, etc. and then wait for 18.04 and do a clean install and add files that I needed. That seemed virtually impossible so I've been limping along with my minimal system while pecking away at the issue.No other window manager will run and many apps also. these seem to be primarily gnome integrated but also firefox, thunderbird and others. (I have been able to run those out of directories instead of the package manager versions.
I lost an entire directory at some point and so was searching. ```
find
```returned no results for it but I did notice that I had many hundreds of "permission denied" lines which was very strange as I was searching my home directory. I could run ```
find
``` as sudo though. After checking the forums I ran ```
chmod 755 *
``` in my home directory and then ```
snip
``` to cover the hidden files and reset the permissions to what they should be. Here are the results of those commands.
```
:~$ chmod 755 *
chmod: changing permissions of 'cairo-dock-plugins-3.4.0': Operation not permitted
chmod: changing permissions of 'core': Operation not permitted
chmod: changing permissions of 'dns-default.txt': Operation not permitted
chmod: changing permissions of 'dns-google.txt': Operation not permitted
chmod: changing permissions of 'http-direct.txt': Operation not permitted
chmod: changing permissions of 'http-dns.txt': Operation not permitted
chmod: changing permissions of 'https-direct.txt': Operation not permitted
chmod: changing permissions of 'libQtCore.so.4': Operation not permitted
chmod: changing permissions of 'libQtGui.so.4': Operation not permitted
chmod: changing permissions of 'libQtNetwork.so.4': Operation not permitted
chmod: changing permissions of 'libQtWebKit.so.4': Operation not permitted
chmod: changing permissions of 'nxdomain-default.txt': Operation not permitted
chmod: changing permissions of 'opt': Operation not permitted
chmod: changing permissions of 'patchlib': Operation not permitted
chmod: changing permissions of 'plugins': Operation not permitted
chmod: changing permissions of 'tr-direct.txt': Operation not permitted
chmod: changing permissions of 'tr-dns.txt': Operation not permitted
chmod: changing permissions of 'xorg.conf.new': Operation not permitted

<snip>

chmod: changing permissions of '..': Operation not permitted
chmod: changing permissions of '.com.zerog.registry.xml': Operation not permitted
chmod: changing permissions of '.fuoco': Operation not permitted
chmod: changing permissions of '.rpmdb': Operation not permitted
chmod: changing permissions of '.subversion': Operation not permitted
chmod: changing permissions of '.Xauthority.bkp': Operation not permitted
ubuntu@ubuntu-laptop:~$ 

```
I figure that somehow in the normal upgrade permissions got seriously messed up and this was what not only caused a Gnome desktop to not function but also the rsync and any number or weird behaviors. Since I've changed the permissions to correct them I'm wondering what these lingering "Operation not permitted" lines are. 
I have little hope of restoring my system but I would like to know how best to proceed in order to keep my data safe. I've lost my VMs (can't run VBox) but luckily didn't have critical data. Any help would be greatly appreciated and as I wrote, I apologize for the length.

---

### Post by QIII on 2018-04-10
Never, EVER, run the command I snipped.  Depending on where you are, that pattern can potentially match the directory hierarchy above your current working directory.  It will certainly match the directory one level up.

Very bad.  If you ran that with sudo, from your home directory or anywhere else, you are surely sunk.

There are directories, even in your home folder, that should not have that permission set.  No problem with them being owned by you, but permissions are another matter.  Blanket changes to permissions can wreak havoc when certain files are expected to have different permissions.

As for recovering your files, do you have a Live ISO on optical media or a USB device?

---

### Post by ubuntubrian on 2018-04-12
Thanks though not good news tho I didn't expect I'd get much of that. I really appreciate that you responded.
After the update borked my system and not getting much luck with help I did as I described pretty much out of desperation. The rsync errors pretty much matched up the errors I was getting. The snip was, unfortunately, a fix that I found in my endless searches on several forums, that resetting home permissions was a good and seemingly normal thing using the commands that I did for permission issues. I'm not defending my ineptitude at all, I am many times.  Hopefully most, if not all of those files in the directory above would require the snip to be run as sudo, which it was not so maybe I'm no worse off (hope, pray..). Things were moving a little weird this morning with networking but everything else seems as it was. I'm sure there are glitches that I've created tho that are going to show up. 
But that's all over with so.. I was given a 16.04 live USB by the guy who "helped" and it will not boot. I can download and burn a live .iso to boot from. I will repost as soon as I succeed in having either bootable media work.

---

### Post by ubuntubrian on 2018-04-12
I was finally able to boot a live USB. DVD did not boot. I'm also going to burn a live cd that has testdisk. Hope that this is helpful. I know I can copy much of my data to a new disk but I'll lo9se config files and much elsw. But that's happened before and I'm still alive and nothing horrible happened!
Thanks again for your help

---

