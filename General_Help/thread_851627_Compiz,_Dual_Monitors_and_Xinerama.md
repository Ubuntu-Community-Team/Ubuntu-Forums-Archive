---
title: "Compiz, Dual Monitors and Xinerama"
date: 2008-07-06
forum: General Help
---

### Post by molex on 2008-07-06
Hi, I am running Ubuntu 8.04 on a newly built machine. I am running a Geforce 8800gt video card powering two monitors and configured a Dual Screen Setup w/ Xinerama using 

```
$sudo nvidia-settings
```

and that seems to be working fine.

However, I want to enable some Compiz eye candy but I seem to be having issues. Whenever I select:

System->Preferences->Appearence->Visual Effects->Extra

I get a popup alert claiming:

"The Composite Extension is not available" and then the Appearence Preferences Window b/c unclickable and unclosable.

My nvidia drivers are installed and my system is completely update.
The eye candy DOES NOT work.

Please help me make it work.

I would be most grateful

---

### Post by stich0602 on 2008-07-06
Try installing the compiz settings manager: "sudo apt-get install compizconfig-settings-manager" (no quotes) and then using that to configure your extra effects.

---

### Post by overdrank on 2008-07-06
> **molex said:**
> Hi, I am running Ubuntu 8.04 on a newly built machine. I am running a Geforce 8800gt video card powering two monitors and configured a Dual Screen Setup w/ Xinerama using 

```
$sudo nvidia-settings
```

and that seems to be working fine.

However, I want to enable some Compiz eye candy but I seem to be having issues. Whenever I select:

System->Preferences->Appearence->Visual Effects->Extra

I get a popup alert claiming:

"The Composite Extension is not available" and then the Appearence Preferences Window b/c unclickable and unclosable.

My nvidia drivers are installed and my system is completely update.
The eye candy DOES NOT work.

Please help me make it work.

I would be most grateful

 I believe you will need to use twinview.
As my title shows  what do I know.    :)
Maybe others with more knowledge will comment.

---

### Post by molex on 2008-07-06
> **overdrank said:**
> Hi and please correct me if I am wrong but compiz will not work with  Xinerama I believe you will need to use twinview.

Well, that explains my problem.
In Twinview problem no longer exists
Now, however, I have two sets of panels and the ones on my secondary monitor are non reactive to clicks

---

