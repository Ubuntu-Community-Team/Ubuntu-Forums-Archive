---
title: "Create my own modified distribution - how?"
date: 2014-02-18
forum: General Help
---

### Post by amjjawad on 2014-02-18
Hi everyone,

I am not a developer so easy on me :)
Also, what I am trying to achieve should be something easy and it is a matter of tweaks and customizations more than anything else. 

What exactly I am trying to do?

1- I am thinking about Xubuntu and Ubuntu GNOME as the systems that I wish to modify as per some specific needs and have an ISO file that one can download and install.

2- Changing all the artwork (default wallpaper) and the slide show and add what I want.

3- Change the name of the system so when someone installs the new modified system, it should read something else than Xubuntu and/or Ubuntu GNOME.

4- Change the default applications (add what I want and remove what I don't).

5- Once done from these modifications, I want to build an ISO, upload it so someone else can download and install.

6- There should be a Live Session - Try xyz before installation.

7- I am 'not' planning to change anything under the hood like the Kernel, etc. Just the settings and the look and feel.

8- Make sure the system is updated so after I install it, it has all the updates at least for what is available before creating the ISO file.


So, how to do all the above?

I am [converting people in real life to Linux]("http://amjjawad.blogspot.com/2014/01/2014-report-project-convert-my.html") (part of [StartUbuntu]("https://wiki.ubuntu.com/StartUbuntu")) and it is giving me extra headache and time to do all the tweaks after the installation. I'm working hard to save my time because I am involved with so many projects and I'm under heavy work.

Also, I am thinking to do this for the city I live in and distribute that system as a way to spread the word of Linux with a system modified for their needs. I know what people here want and like so that would be very helpful.

I am NOT trying to create new project here or new system, it is just a modified system with different settings, applications, look and feel.

For example, what I do after each installation:
1- Install Chromium beside Firefox (the default)
2- Skype
3- VLC
4- LibreOffice (in case of Xubuntu)
5- Shotwell (in case of Xubuntu)
and some other applicaitons

Some people here have kids so need also to include the educations packages.

Hope I have provided all the needed information for you to know what I want to do :)

Thanks in advance!

P.S.
Please don't suggest: [http://www.remastersys.com/](http://www.remastersys.com/)

---

### Post by sudodus on 2014-02-18
Hi my friend,

I think most of the items on your wish-list can be done in OEM mode and then you can port it to another computer via an OBI tarball :-)

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)
[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

But if it is important to change the name of the distro and to make an iso file, you have to remaster the system, which is much more difficult.

---

### Post by amjjawad on 2014-02-18
> **sudodus said:**
> Hi my friend,

Hello my good friend and thanks for posting :)

> I think most of the items on your wish-list can be done in OEM mode and then you can port it to another computer via an OBI tarball :-)

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)
[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)


AFAIK, OBI can't produce an ISO file and needless to say, some very new users to Linux will download and install this modified system either by creating LiveCD/DVD or LiveUSB and AFAIK, OBI can't do that, am I right?


> But if it is important to change the name of the distro and to make an iso file, you have to remaster the system, which is much more difficult.
Indeed, part of my plan is to change the look and feel not for anything except to draw a bigger simile on people faces when they will see a customized system that has been modified for their daily usage.

It shouldn't be harder than creating a new system from scratch or from very basic foundation like [ToriOS]("http://torios.org/") (based on Ubuntu Mini so far)? AFAIK, it should be less headache involved but of course I don't know yet, that is why I'm asking how to do it ;)

Thank you!

---

### Post by ian-weisser on 2014-02-18
> **amjjawad said:**
> Also, what I am trying to achieve should be something easy and it is a matter of tweaks and customizations more than anything else.

I don't see why some of those changes "should" be easy.
What you are asking is very complex. A few years ago, it required a team (or community) of experts to put it all together. Xubuntu required (and still needs) a whole team, and it's not too different from stock Ubuntu. The DE, of course, but mostly art and settings and a few applications.

You never know when a change in the distro that you base on will clobber your minor tweaks. For example, if one of your default applications gets dropped.

Remember also that all those people you help may expect you to support them. The bigger your change from an existing distro, the bigger your support burden.

I found that Debian Live ( [http://live.debian.net]("http://live.debian.org") ) is a great customization tool. It makes maintenance of the custom image easy. But it has quite a learning curve.

---

### Post by amjjawad on 2014-02-20
Hi and thanks for posting :)

> **ian-weisser said:**
> I don't see why some of those changes "should" be easy.
In fact, I didn't mean that would be an easy task, otherwise I would never ask here ;)
I was trying to say, what I am trying to do, IMHO, suppose to be easier than creating something from scratch/nothing. I have a project called [ToriOS]("http://torios.org/") and we're having many challenges and we know it would never be easy but fun and good way to learn :)

> What you are asking is very complex. A few years ago, it required a team (or community) of experts to put it all together. Xubuntu required (and still needs) a whole team, and it's not too different from stock Ubuntu. The DE, of course, but mostly art and settings and a few applications.
Hmm, if that is true and this job will be 'very complicated', then it is a worth to do challenge ;)

>  You never know when a change in the distro that you base on will clobber your minor tweaks. For example, if one of your default applications gets dropped.
I second that. From real experience with many systems for +3 years, you're right. 

>  Remember also that all those people you help may expect you to support them. The bigger your change from an existing distro, the bigger your support burden.
True, that is exactly why I will never touch the technical side or the 'under-the-hood' stuff like Kernel :)

I'm already supporting them. No one here is using Linux except me. Well, that was history. Now, 33 machines are enjoying Linux :) but what I mean is, I am their only support guy so yes, I should not overdo it with the new system :D

> I found that Debian Live ( [http://live.debian.net]("http://live.debian.org") ) is a great customization tool. It makes maintenance of the custom image easy. But it has quite a learning curve.

Isn't this all what I need?
[https://launchpad.net/ubuntu-builder](https://launchpad.net/ubuntu-builder)

I just remembered that a friend of mine told me about it before. 

This is all what I need, right?
Or do I need to do something else? I mean use something else?

Thank you!

---

