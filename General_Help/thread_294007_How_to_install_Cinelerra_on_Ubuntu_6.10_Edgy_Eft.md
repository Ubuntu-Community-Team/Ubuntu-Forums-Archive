---
title: "How to install Cinelerra on Ubuntu 6.10 Edgy Eft"
date: 2006-11-06
forum: General Help
---

### Post by Sabot on 2006-11-06
Open Synaptic

On the menu bar select Settings>Repositories
Click the Third-Party Software Tab
Click the Add button
Enter the repository below:
```
deb http://www.kiberpipa.org/~muzzol/cinelerra/edgy-i386/ ./
```

Close the software sources window and reload your repositories by clicking on the reload button.
Search for Cinelerra by using the search button in Synaptic  and install it.

Cinelerra needs a little extra memory to run in the Kernel.  To add this extra memory you need to edit a file.

Open a terminal and enter the commands below:

```
sudo gedit /etc/sysctl.conf
```

and at the bottom of this text file add the line:

```
kernel/shmmax=0x7fffffff
```

Restart your computer for this new Kernel setting to take effect.

You will find Cinelerra under Applications>Sound & video>Cinelerra.

Now you are ready to enjoy Cinelerra!

One quick note on how I use Cinelerra.  I import using kino from my camcorder. Then I open the dv files with Cinelerra.  After I have made my edits, I render to a raw dv file in Cinelerra.  Kino is used to open and put the video back on my camera. If I want to export to an mpeg file, I use the export feature in Kino.

---

### Post by fsman on 2006-11-06
or even easier use the repos. Add the following to your sources list
(i'm using edgy)

## ubuntu cinelerra [http://cvs.cinelerra.org/getting_cinelerra.html](http://cvs.cinelerra.org/getting_cinelerra.html)
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/) ./

Dapper ones work fine in edgy - no conflict.

---

### Post by hikaricore on 2006-11-06
Just a thought, you might wanna get this moved to the HOWTO's section.  More folks might see it there.  :)

---

### Post by jlx on 2006-11-06
Installation works great, though I still haven't played with it importing and editing videos.
To log as root just type ```
sudo -s -H
``` and then enter your user password.

---

### Post by Sabot on 2006-11-06
Fsman you are linking people to an older version 2.0 and not 2.1.  By the way I use Kino to import and export my files to my DV camcorder.  I have not been able to get the import and export to work in Cinelerra.

---

### Post by jlx on 2006-11-07
I've tried importing avi files and Cinelerra crashes. I think it's not a stable solution to edit video files, at least in Edgy. 
I tried MainActor (there's a demo for Ubuntu) and it works perfect. It's more stable than Cinelerra and more user friendly. You have to import dv files just like Kino. The demo limitation is a watermark on the final edited video. It's expensive but you can use the demo.

---

### Post by Russty of Oz on 2006-11-08
"You will need to be root to issue the command. Sudo will not work."

What do I have to do to do it as root?

---

### Post by Sabot on 2006-11-10
> **Russty of Oz said:**
> "You will need to be root to issue the command. Sudo will not work."

What do I have to do to do it as root?

You need to open a terminal window and enable the root password for ubuntu:

```
sudo passwd root
```

Then once you have a root password type su to become root.

The error that comes up in Cinelerra gives you a command to enter to fix the memory problem.  It starts with echo.  Enter the full command it provides in the terminal window and you are good to go.

---

### Post by Sabot on 2006-11-10
Cinelerra is very crash happy, so save after each edit.  Cinelerra was the only way I could edit indivdual audio tracks on my video.  I only use raw dv and wav files. They seem to work ok.

---

### Post by Dot Communist on 2006-11-12
cinnerella .deb wont install because libmjpegtools0 isint working :(

---

### Post by Dot Communist on 2006-11-12
> **Dot Communist said:**
> cinnerella .deb wont install because libmjpegtools0 isint working :(
it says this when i install the jpegtools0 .deb

subprocess paste killed by signal (broken pipe)

---

### Post by Sunn3K7aas on 2006-11-15
Make sure you don't have any other version of mjpegtools installed already and remove if you do.

---

### Post by Sabot on 2006-11-21
> **Dot Communist said:**
> it says this when i install the jpegtools0 .deb

subprocess paste killed by signal (broken pipe)

Make sure you remove any version of libmjpegtools that is already installed.  You can do this by opening Synaptic and uninstalling the file. Close Synaptic and you can install the one I provided. Just double click the one that is provided in my above post.  You can then install mjpegtools with Synaptic. You will have a broken package error, but Cinelerra will work.

One big issue that I did run into is with the broken package error is you can't install transcode.  You have to uninstall libmjpegtools (the one I provided) and Cinelerra to install transcode.

---

### Post by ossi on 2006-12-06
Hi!

I installed the Cinelerra 2.1 package yesterday and it worked immediately using Kubuntu 6.10. I asked on the Cinelerralist what to do with the mistake. I haven't tried it my own yet but this should be a way to solve it:

```
adding the line 
>
> kernel/shmmax=0x7fffffff
>
> to the (hidden) file /etc/sysctl.conf
>
> For the first time, to avoid restarting my computer, using the command
> (as root)
> 
> $ sysctl -p
```

Of course, use SUDO where needed. This should let the message disappear - but be careful with editing configuration files and probably don't do it when you don't need Cinelerra a lot.

To say something to the offtopic:
I used Kino a long time to but the whole /dev/raw thing made me go mad after a while. Now I use a commandline tool called dvgrab - give it a try, its worth it.

---

### Post by fsman on 2006-12-07
> **Sabot said:**
> Fsman you are linking people to an older version 2.0 and not 2.1.  By the way I use Kino to import and export my files to my DV camcorder.  I have not been able to get the import and export to work in Cinelerra.

Currently cvs.cinelerra.org only has the 2.0 packages for ubuntu.

I too use kino to capture. In preferences try selecting RAW DV as the file type. - works great for me.

---

### Post by ossi on 2006-12-12
There is a new repository for Cinelerra 2.1 and edgy. Add these lines to /etc/apt/sources.list:

 deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main
 deb [http://www.kiberpipa.org/~muzzol/cinelerra/](http://www.kiberpipa.org/~muzzol/cinelerra/) bin/

---

### Post by hrabeX on 2006-12-13
> **ossi said:**
> There is a new repository for Cinelerra 2.1 and edgy. Add these lines to /etc/apt/sources.list:

 deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main
 deb [http://www.kiberpipa.org/~muzzol/cinelerra/](http://www.kiberpipa.org/~muzzol/cinelerra/) bin/

not working :(

---

### Post by mrastas on 2006-12-13
What is not working?

I have trouble finding/installing the key needed to authorize debian repository.

Not anymore [http://www.debian-multimedia.org/faq.html]("http://www.debian-multimedia.org/faq.html")

---

### Post by mrunion on 2006-12-15
The Edgy packages/reposity above still doesn't allow transcode to be installed with cinelerra.  Is that nrmal or has something else on my machin went wonky?

---

### Post by lprofil on 2006-12-18
If you like to know how to compile **Cinelerra 2.1 CV** from subversion sources 
the easy way you might be interested in [my new tutorial for Edgy Eft]("http://www.ubuntuforums.org/showthread.php?p=1899731").

/lprofil

---

### Post by paulhollow on 2007-01-07
Thanks very much for the tutorial!!!!  Works great!  I haven't had much time to play with Cinelerra, but from what i have seen, it looks superb.

BUT...  i have another problem.  I also use DVDStyler to produce/author DVDs - but this has libmjpegtools0c2a as a dependancy.  I removed both libmjpegtools0c2a and DVDStyler in order to install Cinelerra (which uses libmjpegtools0 1:1.8.0-0.4), which worked ok.

I then reinstalled DVDStyler (from Synaptic package manager) but this complained that it could not install libmjpegtools0c2a as it conflicted with libmjpegtools0.

However, both Cinelerra and DVDStyler are now working fine together (both, i guess, using libmjpegtools0, not 0c2a...) but Synaptic package manager is now complaining that it has a broken package and wants to remove libmjpegtools0c2a - but if i let it, it will also remove DVDStyler...which i want to keep...

Is there any way i can make both packages co-exist?  Or can i persuade DVDStyler to use libmjpegtools0 instead of ...0c2a?  Or can i get Synaptic to ignore this one broken package (as at the moment it won't let me install updates)?

Any help appreciated!!!! Thanks in advance!

Paul

---

### Post by cillian.deroiste on 2007-02-16
I installed 2.1 from the repos in the cvs.cinelerra wiki
[http://cvs.cinelerra.org/docs/wiki/doku.php?id=english_manual:cinelerra_cv_en_2#ubuntu](http://cvs.cinelerra.org/docs/wiki/doku.php?id=english_manual:cinelerra_cv_en_2#ubuntu)

I had to uninstall 2.0 with
>  apt-get remove cinelerra
and then remove the dependencies with
> apt-get autoremove

and apt-get install cinelerra with the following in /etc/apt/sources.list
> deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
deb-src [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./

it will also recommend you do:
> echo "0x7fffffff" > /proc/sys/kernel/shmmax
after it starts

Which I believe you can do more permanently by adding:
> kernel.shmmax = 2147483647
to your /etc/sysctl.conf file

To check it  
> cat /proc/sys/kernel/shmmax 
should return:
2147483647

I gather this may lead to instability so please use with caution.

---

### Post by moaxey on 2007-03-25
having a problem with this:

```
$ cinelerra
cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen
```

everything seems to be the right versions and dependencies.

help!

---

### Post by mohnkern on 2007-04-06
This article is now outdated.  Most of the links no longer function.

---

### Post by mateuszbaranski on 2007-04-11
> **Sabot said:**
> Cinelerra is very crash happy, so save after each edit.  Cinelerra was the only way I could edit indivdual audio tracks on my video.  I only use raw dv and wav files. They seem to work ok.

I have been using Cinelerra on Mandriva 2007 for one month. It is no better either. Hangs up every minute :) -  I have comparision to Adobe Premiere Pro - which I have been using for one year which is a rock-stable but it costs a lot of money.

In Cinelerra I have been keeping my two fingers on the ctrl-s all the time  :-(  Thus I have finished one complete movie (but it was captured in Kino which is better at this point) with a success. 
Though the worst part (a nightmare) was to encode the movie into something usable (MPEG2).

Similar problems I encounter in Ubuntu 6.10. but in my opinion it is much more stable (e.g. one crash per 15 minutes :-)  )

Mateusz

---

### Post by 9a3eedi on 2007-04-15
I'm using edgy amd64, and I've been getting some dependency problems when installing cinelerra

Last couple of lines of "sudo apt-get install cinelerra"
```

(Reading database ... 198367 files and directories currently installed.)
Unpacking libmpeg3hv (from .../libmpeg3hv_1%3a2.1.0-2svn20070109_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libmpeg3hv_1%3a2.1.0-2svn20070109_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/mpeg3cat', which is also in package mpeg3-utils
Selecting previously deselected package libquicktimehv.
Unpacking libquicktimehv (from .../libquicktimehv_1%3a2.1.0-2svn20070109_amd64.deb) ...
Selecting previously deselected package cinelerra.
Unpacking cinelerra (from .../cinelerra_1%3a2.1.0-2svn20070109_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libmpeg3hv_1%3a2.1.0-2svn20070109_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

did anybody else get this?

if somebody is interested, in order to get rid of the broken dependency hell, you have to invoke

sudo apt-get remove cinelerra libquicktimehv libmpeg3hv

but that removes it.. at least apt-get works again

I'm going to try make it work from svn :)

---

### Post by cssutto on 2007-06-27
I have installed cinelerra and it looks good.

All I want to do for now is combine several quicktime videos into one large video.

I can't find instructions on how to do that.

Could someone please give me a hint?

CSSJR

---

### Post by Blessed_Coffee on 2007-12-12
```
bash: deb: command not found

```

:confused:

---

