---
title: "Why do I have trouble with Kubuntu, but not Ubuntu?"
date: 2008-05-08
forum: General Help
---

### Post by Afkpuz on 2008-05-08
Let me preface this by saying that I love ubuntu and the linux community.  I have nothing but praise for ubuntu.  However...my feelings for kubuntu are nothing like my feelings for ubuntu.   Every time I have tried out kubuntu, I have been met with numerous errors.  Not setup problems, but straight up errors that should not happen.  For example, when trying kubuntu 7.10, after a fresh install on a separate partition, I went to get some updates.  I was met with an error saying that I couldn't get the updates/apply them.  Try again, no luck.  I've had this problem on EVERY single try of kubuntu and I've tried at least 5 different fresh installs of kubuntu on two different computers.  Whats up with this?  Then I try to listen to some music.  Amarok is an awesome program, but in mid music, it crashes.  I assume that this is not an across the board thing, yet I know my hardware is fine, as ubuntu works great.  I know my internet is fine, and I've checked my install cds for flaws.  So my question is this: why do I have this problem across multiple computers?  Is KDE just not as stable as gnome?  Shouldn't KDE work as well as my gnome install?  

I'm sorry this is a rant, but I see a definite decline in quality from gnome to KDE.  I can't understand why I've had so much trouble with kubuntu.  Anyone else has similar experiences?

---

### Post by Whiffle on 2008-05-08
> **Afkpuz said:**
>   Shouldn't KDE work as well as my gnome install?  



Yes it should, and does, just not in Kubuntu.  Alot of people who have used KDE in places other than Kubuntu (such as myself) have been disappointed at Kubuntu, its just not done right.

---

### Post by ellgor on 2008-05-09
Hi,

You are quite right when you say Kubuntu is a bit flaky, however I have found that instead of installing the Kubuntu package, as is, install the KDE package (sudo apt-get install KDE) I thought they are one and the same but hey the KDE package works a treat (not sure if everything is included though) anyway thats my suggestion to you, hope this helps.

Regards, Ellgor.

---

### Post by Zorael on 2008-05-09
Weird. I'm using Kubuntu exclusively and I haven't had any major issues with it. On the contrary, I find Gnome to be more meh. Even when I ran Ubuntu, before discovering Kubuntu one day when I was bored and thought I'd try out Kubuntu and Xubuntu just for kicks, I was mostly using KDE (Qt) programs since they felt more solid and consistent. I'd remove the GTK libraries if stuff like Firefox, GIMP and **g**mplayer weren't dependent on them. (Don't start about **k**mplayer. It's...inferior.)


I've found a bug or two, sure.
[list][*]Changing background in the Login Manager section of systemsettings/kcontrol breaks login theming (and as such disables the Kubuntu theme). Fixed by not changing background (:>) or restoring default background assignment in **/etc/kde3/kdm/backgroundrc**. Then edit **/etc/default/kdm.d/20_kubuntu_default_setting**.
[*]Impossible to change desktop directory with systemsettings/kcontrol, need to manually edit **~/.config/user-dirs.dirs**. Something like [$E] sneaks in, so remove that bit and all is well. Bug since Gutsy.[/list]

One shouldn't delude oneself that KDE is receiving less developer attention, and as such will fall hopelessly behind; granted, in the *buntus, KDE users are overshadowed by Gnome users, but the global KDE userbase is slightly larger. I was sort of surprised that Canonical chose Gnome to be the standard in Ubuntu, instead of releasing a Gubuntu for die-hards. KDE has a bit of a history though, with the window framework having been proprietary (until it was GPL'd a while back), which may have had a hand in things.

Of course, the KDE vs Gnome discussion will still continue to the end of time.
> [i]G: "Only those who can't live without the Start menu run KDE! gb2/windows" (actually common one)
K: "Gnome is redundant and immature!"
G: "KDE is more well-polished *and* uses less memory!"
K: "KDE suffers from creeping featurism and overwhelms the user!"[/i]

Ad nauseam. Heck, I'm not completely innocent, see the first link in my signature. My point is, if you like KDE, go Kubuntu, install the GTK libraries and use any Gnomey programs you like. If you like Gnome, go Ubuntu, install the Qt libraries and use any KDEy programs you like.

---

