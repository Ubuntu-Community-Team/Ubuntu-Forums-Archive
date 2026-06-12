---
title: "Firefox is gone after Ubuntu update"
date: 2008-04-05
forum: General Help
---

### Post by wawadave on 2008-04-05
Newby here.

I did the updates this morning. After done went to go on the web. there was a sping with platform icon where firefox icon used to be. clicked it an got unable to launch application error.

So opened opera and d/led firefox for link. Though this may be easy to then install this for most of you i see no .deb ending on any thing in its files and folders. no useful info on what to do with this. Any useful hints help links on reinstalling firefox would be helpful!

I then d/led windows version of firefox installed it under wine.
Works generically and functional. but not like the version of firefox that came with ubuntu.

Ubuntu 8.04
                - the Hardy Heron - released in April 2008.
AMD duron 1200 mhz
256 megs of ram
yes ram is under spects for ubuntu short of running open ofice system function fine

This is a test for me to see if i can get bryce,D/S,poser5 to work on here. no luck on any. If i do ever get these to work its bye bye ms. 
But not done yet much to learn.				

---

### Post by y-lee on 2008-04-05
You downloaded the source code for firefox and to use it you would have to compile it, see [Installing software]("http://www.psychocats.net/ubuntu/installingsoftware#source").

But the easiest thing to do would be to open synaptic package manager from your menu under Administration and search for firefox. Once you find to it either install it if it is not installed or reinstall it if it is installed.

however it may be the link is messed up. You could try to find firefox on your system and see if you can start it from there, if so the link is trashed. Look in /usr/bin. If the link is messed up it can be fixed tho honestly reinstalling as above should fix it :)

---

### Post by -grubby on 2008-04-05
Could you try running ```
firefox
``` in the terminal and see if that launches it?

---

### Post by y-lee on 2008-04-05
> **nathangrubb said:**
> Could you try running ```
firefox
``` in the terminal and see if that launches it?

Good point. If that works without any errors the link is messed up. If it gives a bunch of errors and still doesn't work post back with errors.

---

### Post by knutschr on 2008-04-05
Paste into terminal
sudo apt-get install firefox
(You won't see that you type your password.)

---

### Post by JoseReyes on 2008-04-05
> **y-lee said:**
> You downloaded the source code for firefox and to use it you would have to compile it, see [Installing software]("http://www.psychocats.net/ubuntu/installingsoftware#source").

But the easiest thing to do would be to open synaptic package manager from your menu under Administration and search for firefox. Once you find to it either install it if it is not installed or reinstall it if it is installed.

however it may be the link is messed up. You could try to find firefox on your system and see if you can start it from there, if so the link is trashed. Look in /usr/bin. If the link is messed up it can be fixed tho honestly reinstalling as above should fix it :)

I lost firefox 3 also, when I try to install from synaptic  is tellls me this:
firefox-3.0:
 Depends: xulrunner-1.9 but it is not going to be installed

I did not insall firefox 3 outside the repos it was the one that came with hardy heron beta. I am using Hardy Heron 64bit. Any suggestions?

---

### Post by y-lee on 2008-04-05
> I lost firefox 3 also, when I try to install from synaptic is tellls me this:
firefox-3.0:
Depends: xulrunner-1.9 but it is not going to be installed

Install xulrunner first and then install firefox. Use synaptic if it is easiest for you.

---

### Post by brian_p on 2008-04-05
> **JoseReyes said:**
> I lost firefox 3 also, when I try to install from synaptic  is tellls me this:
firefox-3.0:
 Depends: xulrunner-1.9 but it is not going to be installed

I did not insall firefox 3 outside the repos it was the one that came with hardy heron beta. I am using Hardy Heron 64bit. Any suggestions?

xulrunner is not available and without it that version firefox will not install. Could be because Hardy Heron is in a state of flux. The only thing to do would be to wait until xulrunner appears.

If you had a .deb of the previous version on your system you could try installing that with dpkg -i <package.deb>.

---

### Post by jaksh_eet on 2008-04-05
> **JoseReyes said:**
> I lost firefox 3 also, when I try to install from synaptic  is tellls me this:
firefox-3.0:
 Depends: xulrunner-1.9 but it is not going to be installed

I did not insall firefox 3 outside the repos it was the one that came with hardy heron beta. I am using Hardy Heron 64bit. Any suggestions?

I am having the same issues this morning after updating. I am using the Hardy Heron 32bit.

I had to install Opera from Synaptic just to get a browser. And it shows I already have the xulrunner-1.9 already installed and still gives me the same error when trying to install Firefox3.

---

### Post by wawadave on 2008-04-05
> **knutschr said:**
> Paste into terminal
sudo apt-get install firefox
(You won't see that you type your password.)
ok did what you said got this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  firefox: Depends: firefox-3.0 but it is not going to be installed
E: Broken packages

From add remove i get

Cannot install 'firefox-3.0'

This application conflicts with other installed software. To install 'firefox-3.0' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.9



ok i saw synaptic' package manager mentioned above where do i fine this?

i allso trued running firefox n terminal it just quits.

---

### Post by jaksh_eet on 2008-04-05
I wonder if this is due to Firefox 3 Beta 5 release today.

[HTML]http://developer.mozilla.org/devnews/index.php/2008/04/02/firefox-3-beta-5-now-available-for-download/[/HTML]

---

### Post by tamoneya on 2008-04-05
Thats what I was hoping for.  beta 5 was released a couple of days ago and my firefox hasnt updated it self.  Who maintains the repositories.  Is there someone we can contact on the development team who would be able to tell us when this will be merged into the repo.

---

### Post by tamoneya on 2008-04-05
it seems to be fixed ```
tamoneya@ubuntu0:~$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  firefox firefox-3.0 firefox-3.0-gnome-support firefox-gnome-support
  xulrunner-1.9 xulrunner-1.9-gnome-support
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.2MB of archives.
After this operation, 168kB disk space will be freed.

```

---

### Post by jaksh_eet on 2008-04-05
Awesome, the new Firefox 3 Beta 5 is working great.

All i had to do was:

```
sudo apt-get update
```

then

```
sudo apt-get install firefox
```


andI have my firefox back. Thanks everyone.

---

### Post by wawadave on 2008-04-05
Ok synaptic package manager fixed this for me!!
 thank you all for your kind help!!!

and it looks like i now have bets 5 as well!!

---

### Post by knutschr on 2008-04-05
Paste into terminal
sudo synaptic

(If this is first time, then also find 'repositories', enable them and reread).

---

### Post by LostAndFound on 2008-04-06
I had a similar issue
"firefox: Depends: firefox-3.0 but it is not going to be installed" etc.

At first sudo apt-get upgrade did not work, but first I did 
sudo apt-get update
then;
sudo apt-get upgrade

and then reinstalled Firefox (through Synaptic in order to get all the related packages like 
firefox-3.0-gnome-support and the web-developer plugin etc)

---

### Post by ayllu on 2008-04-06
I have, the same problem, bur type in your direct acces propietis and change the command for firefox-2 so its works. But i Get the firefox 2 after de hardy uptdate, and  has firefox 3, soo something hapends, and i try to installas firefox 3 but i coudnt. So any one can solve the problem.

---

### Post by ayllu on 2008-04-06
The fact is, for some reason I don't know why the update install firefox 2 so, you need to go to synaptic so unistall firefox2 first, then install firefox3 so its will work again.

---

