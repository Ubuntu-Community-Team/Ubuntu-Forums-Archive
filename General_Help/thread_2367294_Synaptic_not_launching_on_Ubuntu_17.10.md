---
title: "Synaptic not launching on Ubuntu 17.10"
date: 2017-07-28
forum: General Help
---

### Post by Hasimir on 2017-07-28
I just installed Ubuntu 17.10
Everything seems to be working quite ok, except that I'm unable to use Synaptic.
I installed it with (apparently) no problems, but when I click its icon, nothing happens.
Trying from the terminal this is the error I get:

No protocol specified
Unable to init server: Could not connect: Connection refused
(synaptic:3572): Gtk-WARNING **: cannot open display: :0

Any idea what this means? :P

Thanks in advance for the support :)

---

### Post by #&amp;thj^% on 2017-07-28
This has been disused a few times now here.
Enter this in the terminal:
```
xhost +si:localuser:root
```
This will give synaptic a temporary permission for this session only.
[s]This thread would be a better fit in Ubuntu Development Version.[/s]
Reached Release.

---

### Post by Hasimir on 2017-07-28
I searched but I failed to find this info. Sorry for the redundant post. And thanks a lot for the quick reply and help :)

---

### Post by #&amp;thj^% on 2017-07-28
No Worries.
And your welcome. :)

---

### Post by Cavsfan on 2017-08-21
Is this solved because as of today Monday August 21, 2017 Synaptic does open without doing anything extra.

I just tried it and it opens after updates and a reboot.

---

### Post by amano on 2017-08-21
Hmm. Maybe you are on X without noticing?

I didn't see any Synaptic related changes the last days/week.

---

### Post by dino99 on 2017-08-21
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1712089](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1712089)

---

### Post by P-I H on 2017-08-21
After upgrade I had to reboot to get the new functionality
The login alternatives have changed to
- Ubuntu
- Ubuntu on Xorg

I made login to Ubuntu and checked if the applications I'm mostly use still work. I checked
- Synaptic
- Kodi in snap version
- Steam with CIV IV
- Handbrake
- Chromium
- Gmail
- Gedit
- Tweaks
- Software
All worked fine
However there seems to be a problem with logout and login

---

### Post by harry332 on 2017-08-22
After updating my setup the same issue with synaptic here too.
I use only gnome-session and the gnome wayland session was automatically chosen.
Well, I changed the session to gnome on Xorg.
Now synaptic works again without any command line tricks after every boot.

This is the update I am talking about:
gdm3 (3.25.90.1-0ubuntu2) artful; urgency=medium   * debian/patches/ubuntu_prefer_x11_session.patch:
    - remove x11 session preference now that both Ubuntu and GNOME
      switched to wayland

---

### Post by Cavsfan on 2017-08-22
Yes, you are correct I managed to get a Gnome Classic session installed and it would seem it would be Wayland but, it was in an X11 session.
I have these options when logging in:
[LIST=1]
[*]Gnome
[*]Gnome Classic
[*]Gnome on Xorg
[*]Ubuntu
[*]Ubuntu on Xorg
[/LIST]

The first is definitely Wayland and 2 and 3 are Xorg. Option 4 is Wayland and 5 is as it states Xorg.

Synaptic did not open on any Wayland sessions I tried.

Guess I forgot Synaptic opens normally on an Xorg session.

---

### Post by ventrical on 2017-08-22
On the 8/22 daily it is just:
Ubuntu
Ubuntu on Wayland

Thats it.

---

### Post by ventrical on 2017-08-22
Works on xorg, not wayland. They're working on it.

---

### Post by jbicha on 2017-08-23
Sadly, nobody is really working on Synaptic for GNOME/Ubuntu on Wayland support.

---

### Post by fthx on 2017-08-24
That's really a problem. I stay with X just to have Synaptic working because a lot of changes are pending now.
On the French forum, roughly everybody find Synaptic is essential, looking at the incomplete job of GNOME Software app.

And not everybody is aware of how to do the required changes in the Synaptic's code !! ;-) 

Please note that the recent experience I have with some newbies colleagues seems to prove that Synaptic is not a geek tool only. I can say them "install xxx package from Synaptic", sagemath e.g., and there is no problem. Instead, Software does not even find this package. Frankly speaking, with all the respect for the dev work I have, it's a BIG issue.

---

### Post by dino99 on 2017-08-24
> **fthx said:**
> That's really a problem. I stay with X just to have Synaptic working because a lot of changes are pending now.
On the French forum, roughly everybody find Synaptic is essential, looking at the incomplete job of GNOME Software app.

And not everybody is aware of how to do the required changes in the Synaptic's code !! ;-) 

Please note that the recent experience I have with some newbies colleagues seems to prove that Synaptic is not a geek tool only. I can say them "install xxx package from Synaptic", sagemath e.g., and there is no problem. Instead, Software does not even find this package. Frankly speaking, with all the respect for the dev work I have, it's a BIG issue.

There is no need to tweak the synaptic code to get it working with wayland :confused:
Simply click on the link found into comment #7 and copy/paste the given script into a terminal.
That it, do it once after each cold boot.

---

### Post by ventrical on 2017-08-24
> **fthx said:**
> That's really a problem. I stay with X just to have Synaptic working because a lot of changes are pending now.
On the French forum, roughly everybody find Synaptic is essential, looking at the incomplete job of GNOME Software app.

And not everybody is aware of how to do the required changes in the Synaptic's code !! ;-) 

Please note that the recent experience I have with some newbies colleagues seems to prove that Synaptic is not a geek tool only. I can say them "install xxx package from Synaptic", sagemath e.g., and there is no problem. Instead, Software does not even find this package. Frankly speaking, with all the respect for the dev work I have, it's a BIG issue.

It's am awesome tool. I am going to research it. If I can fix it I will.

---

### Post by fthx on 2017-08-24
@dino
It depends on what you mean by "working with". I can switch to a X Ubuntu session, work with Synaptic and go back to Wayland. I can use your workaround too.
But the goal is IMHO to have a real fix to *work with* Wayland.

---

### Post by ventrical on 2017-08-24
So it is this:

```

(2) synaptic nowadays is built with gtk+ 3, so should run natively under Wayland, but


$ /usr/sbin/synaptic


segfaults:

Program terminated with signal SIGSEGV, Segmentation fault.
#0  0x00007fa743155cc0 in wl_display_interface ()
    at /usr/lib/x86_64-linux-gnu/libwayland-client.so.0
#1  0x00007fa7496b5af9 in XSync (dpy=0x561939e12100, discard=discard@entry=0)
    at ../../src/Sync.c:42
#2  0x000056193905ba6b in RGFlushInterface() () at rgutils.cc:68
#3  0x000056193906a73e in RGMainWindow::buildInterface() (this=this@entry=0x561939e645b0) at rgmainwindow.cc:973
#4   0x000056193906cb68 in RGMainWindow::RGMainWindow(RPackageLister*,  std::__cxx11::basic_string<char, std::char_traits<char>,  std::allocator<char> >) (this=0x561939e645b0,  packLister=0x56193a103550, name="") at rgmainwindow.cc:815
#5  0x00005619390467c2 in main(int, char**) (argc=<optimized out>, argv=<optimized out>) at gsynaptic.cc:462


The  reason is the explicit call to XSync. If I remove that, it works  natively under Wayland. But only as non-root, as pkexec doesn't work on  Wayland.


Cheers, Roderich 



```


meaning that this:

```

$ xhost +si:localuser:root

```
is the only current workaround.

edit

but this I think would fix it  but that would be up to the maintainer , no?
> 
synaptic should really look at adding polkit support to gain the root 
privileges instead of running the full ui as root




edit:

So it appears that synaptic has to be "allowed'  in the polkit

```

As a       result, **pkexec** will not by default allow you to run       X11 applications as another user since       the $DISPLAY and $XAUTHORITY       environment variables are not set. These two variables will be retained       if the *org.freedesktop.policykit.exec.allow_gui* annotation       on an action is set to a nonempty value; this is discouraged, though, and       should only be used for legacy programs.     

```

---

### Post by dino99 on 2017-08-24
comment #7 also list a fedora link inside the report, where there is a more sophisticated (not tested myself) idea to insert that script into bashrc. That is known sadly that synaptic is slowly abandonned.

wiki: [https://fedoraproject.org/wiki/Common_F25_bugs#wayland-root-apps](https://fedoraproject.org/wiki/Common_F25_bugs#wayland-root-apps)

reports:
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=818366](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=818366)
[https://bugzilla.redhat.com/show_bug.cgi?id=1274451](https://bugzilla.redhat.com/show_bug.cgi?id=1274451)

In order to make an application using pkexec available in Wayland, it is necessary to migrate from pkexec to polkit. 

Well-known applications affected by this are "synaptic", "gparted", "ubiquity".

---

### Post by ventrical on 2017-08-24
> **dino99 said:**
> comment #7 also list a fedora link inside the report, where there is a more sophisticated (not tested myself) idea to insert that script into bashrc. That is known sadly that synaptic is slowly abandonned.

Yes .. and it's really not my place to override another maintainer. But if I can find a feasible workaround within a standard ubuntu file .. i will.

Thanks dino

---

### Post by ventrical on 2017-08-24
> **dino99 said:**
> comment #7 also list a fedora link inside the report, where there is a more sophisticated (not tested myself) idea to insert that script into bashrc. That is known sadly that synaptic is slowly abandonned.

If you use gksu it will note that it is trying to write to file.xauthority (MAGIC COOKIE) but fails. There is no .xauthority file by default in a fresh install in /home.

 I can see that the bashrc method might cause probs down the road on a development install.

---

### Post by Chanath on 2017-08-24
Synaptic gets installed and works very well in Unity, Gnome-Flashback, Xubuntu and Openbox. All are 17.10. 
Should such a good app be dropped for still unknown Wayland?

---

### Post by rrnbtter on 2017-08-24
Greetings,
Wayland is part of the reality of things and some people dread change.  However is is up to the application developer to make the application work or not. This is no different than what we encountered with Grub2, UEFI, Systemd, and etc. My wife doesn't have a problem.  She just uses her computer and never complains. Most of the problems are due to the users that want to play under the hood. Just like auto's, tv's computers and everything else, there will be change and a mind tax.

---

### Post by ventrical on 2017-08-24
> **Chanath said:**
> Synaptic gets installed and works very well in Unity, Gnome-Flashback, Xubuntu and Openbox. All are 17.10. 
Should such a good app be dropped for still unknown Wayland?

I've been doing a lot of reading on wayland and as it stands (at least in Fedora) it is very feeble when coming to running legacy apps such as synaptic. (Seems the same applies in the ubuntu-gnome-wayland set.)  One's first inclination might be to think that end_users are being corralled  to the Software Center if they want workable facsimile apps to run on wayland but we  got to give it time . I am working on this.  Wayland (current) is a very interesting read. 

:note:

btw .. I did try the  Weston nested workaround and it flopped so that inidcates that there is something wrong with compositor or the way that GTK 3 is wrapping the program. One good thing is that synaptic is wayland wise but there is a polkit problem and the maintainer has to get on the program with this and we can't point to current dev as being the problem here.

I am doing some experiments with kde atm . will get back if anything..

---

### Post by ventrical on 2017-08-24
> **rrnbtter said:**
> Greetings,
Wayland is part of the reality of things and some people dread change.  However is is up to the application developer to make the application work or not. This is no different than what we encountered with Grub2, UEFI, Systemd, and etc. My wife doesn't have a problem.  She just uses her computer and never complains. Most of the problems are due to the users that want to play under the hood. Just like auto's, tv's computers and everything else, there will be change and a mind tax.

Well.. agreed .. but we as testers have to try and break it, hammer it  and bend it if we want it  to be a quality product. If we feather it and corner-case it  then it will be suffice to say it will remain feeble and wanky. If we stop looking under the hood we might as well go back to windows :) and we all know what kind of fun that was. :(

Regards..

---

### Post by rrnbtter on 2017-08-24
Greetings,
@Ventrical: Yes, and if someone takes a hammer and breaks it they should be happy that it is broken. That is the purpose of this section.  If you download an image and it doesn't install you can report it or not, that is the purpose of this section. But to complain that it doesn't work or that there is something new is not the purpose of this section. As I have said before, I have used the dev version with proposed enabled for the entire seven years I have used linux. I have done thirty of forty reinstalls as a result. But I did it because I wanted the experience. No complaints here about anything. In fact I think Ubuntu Gnome on Wayland is the most magnificent Os to hit the planet in the last six billion years.  I'm grateful not perplexed. If it has problems, be patient. They will fix it, or not!

---

### Post by ventrical on 2017-08-24
> **rrnbtter said:**
> Greetings,
@Ventrical: Yes, and if someone takes a hammer and breaks it they should be happy that it is broken. That is the purpose of this section.  If you download an image and it doesn't install you can report it or not, that is the purpose of this section. But to complain that it doesn't work or that there is something new is not the purpose of this section. As I have said before, I have used the dev version with proposed enabled for the entire seven years I have used linux. I have done thirty of forty reinstalls as a result. But I did it because I wanted the experience. No complaints here about anything. In fact I think Ubuntu Gnome on Wayland is the most magnificent Os to hit the planet in the last six billion years.  I'm grateful not perplexed. If it has problems, be patient. They will fix it, or not!

@rrnbtter

I have no problem giving you all those points above. Fixes will come. No doubt. However I think it is ok to have some fair commentary because it helps those of us doing some of the heavy lifting to de-compress a little :) We can work and have a little fun in the meantime. I do not see some of the comments as complaints or charmers but , rather pointers to possible future bug reports and progress reports to encourage  developers on .  We can still have due dilligence and fair commentary  and leave the wholly forensic stack  to the launchpad. Thats why its there.

But I do appreciate your comments as a pointer to stay on the beam and be  purposefully oriented.

Regards..

---

### Post by jbicha on 2017-08-24
Why don't you give gnome-packagekit a try?

---

### Post by Chanath on 2017-08-24
Synaptic is used for quite a long time. App Shops won't find some apps, for example chrome-gnome-shell - something quite needed.
In my installs, Synaptic works. In Synaptic, you can find all apps that are in the repos.

---

### Post by ventrical on 2017-08-24
> **jbicha said:**
> Why don't you give gnome-packagekit a try?

I have just spent a large amount of time trying out

```

policykit-1-gnome

```

but it breaks the desktop.

You can recover the desktop .. etc.. but it replaces policykit-1 with policykit-1 :i386. So you have to remove and install policykit-1 again.

I'll try the package you mentioned.

---

### Post by ventrical on 2017-08-24
> **jbicha said:**
> Why don't you give gnome-packagekit a try?

Ahhh .. a gnome version of synaptic.  Looks nice.  I can get used to it.

[https://bugs.launchpad.net/ubuntu/+source/gnome-packagekit/+bug/1712914](https://bugs.launchpad.net/ubuntu/+source/gnome-packagekit/+bug/1712914)

---

### Post by mc4man on 2017-08-24
> **jbicha said:**
> Why don't you give gnome-packagekit a try?

It would be nice if it had a history..
Does seem pretty easy to get it 'stuck' (a race?), example in screen shows it running though I closed it out some time ago

---

### Post by jbicha on 2017-08-24
> **ventrical said:**
> I have just spent a large amount of time trying out

```

policykit-1-gnome

```

but it breaks the desktop.



If you read the [package description for policykit-1-gnome]("https://packages.debian.org/unstable/policykit-1-gnome"), you'll see that it's not a package for GNOME any more.

Fixing Synaptic is really a project for an app developer, but for a lot of reasons it's not a very interesting thing for app developers to work on. For one, app developers don't tend to use Synaptic&#8230;

---

### Post by mc4man on 2017-08-24
> **mc4man said:**
> It would be nice if it had a history..

Appears it keeps logs, not accessible thru the gui itself
gpk-log

---

### Post by ventrical on 2017-08-24
> **mc4man said:**
> It would be nice if it had a history..
Does seem pretty easy to get it 'stuck' (a race?), example in screen shows it running though I closed it out some time ago

Works great here in wayland.

Has bugs.

---

### Post by ventrical on 2017-08-24
> **jbicha said:**
> If you read the [package description for policykit-1-gnome]("https://packages.debian.org/unstable/policykit-1-gnome"), you'll see that it's not a package for GNOME any more.

Fixing Synaptic is really a project for an app developer, but for a lot of reasons it's not a very interesting thing for app developers to work on. For one, app developers don't tend to use Synaptic…

It is legacy tool for a lot of enthusiasts and bug-fixers alike but I can see why devs don't use it.

Regards..

---

### Post by kurt18947 on 2017-10-01
I just installed and updated 17.10 and had the same problem with Synaptic as previously mentioned - click on it, enter the appropriate password and nothing. So far, if X rather than Wayland is selected in the sudo enabled account, Synaptic launches and works. So the sudo account defaults to X and the user account to Wayland. It seems to work pretty well on modest hardware - ThinkPad X61 core2duo w/ 3 GB RAM. I've been an Ubuntu Gnome user so not a lot of surprises. Gnome Shell Extensions didn't work initially but one line in a terminals seems to have sorted that.

---

### Post by Cavsfan on 2017-10-01
Xubuntu does not have an option to choose between wayland and X.org.
It just boots X,org so Snaptic always just opens up when called upon.

---

### Post by kisina2 on 2017-10-11
This worked for me


> **1fallen said:**
> This has been disused a few times now here.
Enter this in the terminal:
```
xhost +si:localuser:root
```
This will give synaptic a temporary permission for this session only.
This thread would be a better fit in Ubuntu Development Version.

---

### Post by 3togo on 2017-10-11
> **1fallen said:**
> This has been disused a few times now here.
Enter this in the terminal:
```
xhost +si:localuser:root
```
This will give synaptic a temporary permission for this session only.
This thread would be a better fit in Ubuntu Development Version.


Better check whether wayland is really running before granting root right

```
if [ $XDG_SESSION_TYPE = "wayland" ]; then
	xhost +si:localuser:root
fi

```
type the following at the bash prompt will do the trick
```
echo -e "if [ $XDG_SESSION_TYPE = \"wayland\" ]; then\n xhost +si:localuser:root \nfi" >> ~/.bashrc

```

---

### Post by Cavsfan on 2017-10-12
Nice [COLOR=#000000]3togo, I wonder why Xubuntu has no ties to or options for Wayland. Not that I want it but, I thought 17.10 was at least partly about switching to Wayland from X.org. [/COLOR]

---

### Post by jbicha on 2017-10-12
@Cavsfan, many times when we talk about "Ubuntu", we are talking about the default desktop flavor of Ubuntu.

For instance, another new feature in Ubuntu 17.10 is Captive Portal support but only the Ubuntu (GNOME) desktop has integrated a mini-browser for the feature to work.

Only 2 desktop environments support Wayland: GNOME and KDE. It sounds like the MATE developers are hoping to use Mir to get Wayland support a bit quicker. If that works, I expect Xfce and others to use that method too.

---

### Post by Cavsfan on 2017-10-12
> **jbicha said:**
> @Cavsfan, many times when we talk about "Ubuntu", we are talking about the default desktop flavor of Ubuntu.

For instance, another new feature in Ubuntu 17.10 is Captive Portal support but only the Ubuntu (GNOME) desktop has integrated a mini-browser for the feature to work.

Only 2 desktop environments support Wayland: GNOME and KDE. It sounds like the MATE developers are hoping to use Mir to get Wayland support a bit quicker. If that works, I expect Xfce and others to use that method too.

Thank you very much for that explanation. That makes sense.

---

### Post by roadrash on 2017-10-25
I just installed Ubuntu 17.10 from Ubuntu website and installed synaptic as I always do with every install.
For the first time ever it refused to run and I found this link when I searched the error given in terminal.  Is this a bug that needs reported because surely this should run straightaway after install like it always has done until this new 17.10 version.

---

### Post by Cavsfan on 2017-10-25
> **roadrash said:**
> I just installed Ubuntu 17.10 from Ubuntu website and installed synaptic as I always do with every install.
For the first time ever it refused to run and I found this link when I searched the error given in terminal.  Is this a bug that needs reported because surely this should run straightaway after install like it always has done until this new 17.10 version.

Wayland is the default and certain things do not work without the patch mentioned in post [#2]("https://ubuntuforums.org/showthread.php?t=2367294&p=13670516#post13670516") of this thread.

If you login in with an X.org session, it will work as expected.

---

### Post by vasa1 on 2017-10-25
Moved to General Help.

---

### Post by Paloseco on 2017-11-05
> **1fallen said:**
> This has been disused a few times now here.
Enter this in the terminal:
```
xhost +si:localuser:root
```
This will give synaptic a temporary permission for this session only.
This thread would be a better fit in Ubuntu Development Version.

Thanks it works perfectly!

---

### Post by antilight2 on 2018-02-06
> **1fallen said:**
> This has been disused a few times now here.
Enter this in the terminal:
```
xhost +si:localuser:root
```
This will give synaptic a temporary permission for this session only.
[s]This thread would be a better fit in Ubuntu Development Version.[/s]
Reached Release.

Is there a permanent solution or do I have to wait until developers update the software a.k.a. fix the error?

---

