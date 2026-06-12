---
title: "Is Gaim 1.5.0 in Ubuntu out yet?"
date: 2005-09-20
forum: General Help
---

### Post by ppl on 2005-09-20
Last night I get stucked by a autopack installation of Gaim ](*,)

---

### Post by DancingSun on 2005-09-20
[QUOTE=ppl]Last night I get stucked by a autopack installation of Gaim ](*,)[/QUOTE]
It doesn't install?

---

### Post by ppl on 2005-09-20
It was installed, but I am not very happy about the new version installed, I think the dir are different from gaim installed by Ubuntu, it is working but complain about no sound file or something. and I am afraid  it might be not compatible with Synaptic update, then decide unstalled it from autopack, after that autopak crushed.
I think to be safe I will wait Ubuntu to update it if they are ever goint to do it in Ver5.04. It is more than one month already after the gaim 1.5.0 released!

---

### Post by DancingSun on 2005-09-20
[QUOTE=ppl]It was installed, but I am not very happy about the new version installed, I think the dir are different from gaim installed by Ubuntu, it is working but complain about no sound file or something. and I am afraid  it might be not compatible with Synaptic update, then decide unstalled it from autopack, after that autopak crushed.
I think to be safe I will wait Ubuntu to update it if they are ever goint to do it in Ver5.04. It is more than one month already after the gaim 1.5.0 released![/QUOTE]
Well, the thing about the official Ubuntu repositories is that they don't get updated once a released is made.  So you can't expect the official repositories to have the latest thing when it comes out.  It's one of the drawbacks of having centralized package repositories.

However, it is possible to get new version of packages when they are included in the development version of Ubuntu.  In which case, you can request the Official Ubuntu Backports team to backport the package to make it available for the current stable release.  But if current development release (Breezy) does not have GAIM 1.5.0, you won't be able to get it from any of the official repositories.

So if you really want to use GAIM 1.5.0, you'll have to rely on a third party to provide the installation.  What's this problem with sound on the autopackage installation? What's the error during uninstall?  I've heard of people using it without problems.

---

### Post by ppl on 2005-09-20
Thanks for reply!

About the Autopack, I think I might did something wrong, but can' fixed it after that.

The install went through quite smooth, and I did remove Gaim  in synaptic as autopack required, however, I didn't remove gaim data as well; don't know it is part of gaim. After the install, I found two gaim in my manu.and the Synaptic showed I have no gaim installed, I was thinking after that, gaim will not included in my update, which I don't like, even though in fact I could have two version installed and I can pick whatever which one I like, I don't want thing get complexed in my Ubuntu. So I uninstall all gaim and gaim data and plugins from Synaptic searched result, leaving the autopackage installed untouched. 

After I run the gaim 1.5.0 installed by autopackage, I found the buddy list missing icons for my buddies, and it will pop up a small windows saying "no sound" and somthing like missing sound file in directory, I guess it is because gaim in Ubuntu and autopackage are installed in two different directory, and maybe also because I remove gaim data after gaim was installed by autopack. After a while I decided to uninstall gaim from autopack and using gaim 1.4.0 instead. The uninstall looks working as well, except tooks quite long, I think I just closed it after a while, and  
didn't see anything saying uninstall success, that might be the problem as well.
Anyway gaim disappear from manu. When I tried to run autopack manage from my Manu, it broken. The manager will jumb up and doing application search forever, I can't install package for autopackage any more, and I couldn't remove autopackage by command line from autopack faq, it will no response after I input the command line. 

I am waiting for autopack forum guys' suggestion , otherwise I will try to delete it manually, not sure how to do that though.

---

### Post by bryan986 on 2005-09-20
I used the 1.5.0 source to make/install and that worked great for me :)

---

