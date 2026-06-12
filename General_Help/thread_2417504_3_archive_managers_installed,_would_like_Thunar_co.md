---
title: "3 archive managers installed, would like Thunar context menus, informal advice"
date: 2019-04-23
forum: General Help
---

### Post by dez93_2000 on 2019-04-23
Hi all, not a particularly technical one - I have
Engrampa 1.20.1
Archive Manager 3.30.1 and
Xarchiver 0.5.4.13

on my xubuntu 18.10 system, none of which seem to give me Thunar context menu options. [It seems]("https://ubuntuforums.org/showthread.php?t=1258757") that Xarchiver integrates with underlying tools like 7z which I like;
In general can anyone suggest the best program(s) to use so that I can ditch the others? And which would give me context menu options?
Thanks!

---

### Post by &amp;KyT$0P# on 2019-04-23
I use Xarchiver.  Of the archive managers you mentioned, I found Xarchiver integrates best with thunar-archive-plugin / Thunar context menus.
(Not sure if still the case with 18.10, but on 18.04 it needs a small manual tweak as per [this post]("https://ubuntuforums.org/showthread.php?t=2384394&p=13756447&viewfull=1#post13756447").)

---

### Post by Holger_Gehrke on 2019-04-23
Archive manager integration in Thunar is done through a plugin for Thunar. It's available as 'thunar-archive-plugin' from the standard repositories. After installing the plugin take a look at it's README file in /usr/share/doc/thunar-archive-plugin/ for details on how to integrate other archive managers than file-roller (Gnome Archive Manager).

Holger

---

### Post by dez93_2000 on 2019-04-23
Thanks both. Just to be sure, if I go with xarchiver, are we aware of any risks from removing the other two? Cheers

---

### Post by &amp;KyT$0P# on 2019-04-23
> **dez93_2000 said:**
> Just to be sure, if I go with xarchiver, are we aware of any risks from removing the other two?

I have done this on my own Xubuntu 18.04 systems and have not had any issues from it.

---

### Post by dez93_2000 on 2019-04-23
Cheers boss, I'll have at it.

---

### Post by dez93_2000 on 2019-04-24
> **halogen2 said:**
>  with thunar-archive-plugin / Thunar context menus. (Not sure if still the case with 18.10, but on 18.04 it needs a small manual tweak as per [this post]("https://ubuntuforums.org/showthread.php?t=2384394&p=13756447&viewfull=1#post13756447").)

Hi again Halogen,

Did yours just start working whne you made that change or did some of the context plugins work already? It looks like Thunar plugins may be defunct? There doesn't seem to be any way to download them any more, that I can see. I still have my old archive plugin (probably need to do a fresh install one of these years!) but it doesn't seem to work. If you have any thoughts/experience with this I'd be grateful to hear it. Thanks again!

---

### Post by &amp;KyT$0P# on 2019-04-24
> **dez93_2000 said:**
> I still have my old archive plugin (p

"old archive plugin"?  Uninstall that, and reinstall the stock Ubuntu thunar-archive-plugin from standard Ubuntu repositories -
```
sudo apt-get --reinstall install thunar-archive-plugin
```

You might have to re-apply the manual tweak after this.

I'm not sure if you will also need to restart Thunar, you can do it from Terminal -
```
Thunar -q
Thunar --daemon &
```

---

### Post by dez93_2000 on 2019-04-24
Thanks. Sorry for poor wording - I already (probably) stock Ubuntu thunar-archive-plugin installed but reinstalled to be sure; the .tap file didn't change in doing so (i.e. "-d" edit remained).

I wonder if this is because I'm on the 1.8.4git-UNKNOWN version on Thunar but... I doubt it? Their dev branch seems stable and it [doesn't look like]("https://github.com/xfce-mirror/thunar/blob/master/NEWS") plugin support has been deactivated... But in testing other plugins it seems media-tags is installed & current but doesn't work. I installed via .configure style process from git zip downloaded to /home... Dpkg grep thunar says it & plugins are installed but I don't know if that's going to tell me whether it's installed in a way that can't access plugins properly?

---

