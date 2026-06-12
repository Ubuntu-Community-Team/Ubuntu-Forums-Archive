---
title: "[SOLVED] gparted problems"
date: 2008-06-24
forum: General Help
---

### Post by Yondergod22 on 2008-06-24
I download the gparted liveUSB, and ran it, and made my ubuntu partition about 500 mb smaller and my swap bigger. and now when I try boot up my desktop picture loads, but not any icons, or the bars on the top and bottom of the screen. before I completely reinstall, is there any way I can fix it, or at least save all my stuff? 

Thanks in Advance

---

### Post by afbase on 2008-06-24
what does this return:

```
sudo fdisk -l
```

---

### Post by Yondergod22 on 2008-06-24
> **afbase said:**
> what does this return:

```
sudo fdisk -l
```
nothing loads, so I don't have a terminal. im on my xp partition right now.

---

### Post by molotov00 on 2008-06-24
Are you running basic ubuntu? (i.e. not kubuntu or xubuntu)

Take a deep breath. The desktop is one small part of ubuntu. Even in a worse case scenario you can reinstall the desktop without reinstalling the entire OS.

Are you running compiz or anything else fancy? Or just gnome?

I wouldn't do this without getting some other advice that might be less radical... but... doing 'sudo apt-get purge gnome-core xorg' (and other packages, I don't know all of them off-hand) would completely remove your GUI.

Then you could re-install the GUI. Furthmore purging 'ubuntu-desktop' would completely wipe your desktop but not your personal files. It's radical but I'm just trying to illustrate that these options would definitely fix your problem, are radical, and yet would not require a complete reinstall.

Edit: When you say "nothing loads" what happens when you do: ctrl+alt+backspace? That should restart X.

---

### Post by Yondergod22 on 2008-06-24
> **molotov00 said:**
> Are you running basic ubuntu? (i.e. not kubuntu or xubuntu)

Take a deep breath. The desktop is one small part of ubuntu. Even in a worse case scenario you can reinstall the desktop without reinstalling the entire OS.

Are you running compiz or anything else fancy? Or just gnome?

I wouldn't do this without getting some other advice that might be less radical... but... doing 'sudo apt-get purge gnome-core xorg' (and other packages, I don't know all of them off-hand) would completely remove your GUI.

Then you could re-install the GUI. Furthmore purging 'ubuntu-desktop' would completely wipe your desktop but not your personal files. It's radical but I'm just trying to illustrate that these options would definitely fix your problem, are radical, and yet would not require a complete reinstall.

Edit: When you say "nothing loads" what happens when you do: ctrl+alt+backspace? That should restart X.
its just regular ubuntu 8.04, just gnome, and ill go try ctrl+alt +backspace right now.

---

### Post by Yondergod22 on 2008-06-24
ctrl+alt+backspace goes to the login screen, and I get an orange screen when I log in. 
and I went in recovery mode and did "sudo fdisk -l" and its too long the write down, but it does have all my partitions there.

---

### Post by molotov00 on 2008-06-24
I've been digging around and turned up a few instances of people who ran this:
```
sudo apt-get install ubuntu-desktop
```
They saw the desktop start working again. I'd definitely try that if I were you.

Then I was looking for how people uninstalled gnome. I found that uninstalling ubuntu-desktop does not uninstall gnome, which I was surprised about. To get rid of gnome it looks like you want to remove gnome-base. [Edit] I'd do this if i were you, because if you get the login but nothing after it's probably a gnome issue[/edit]
```
sudo apt-get purge gnome-base
#then
sudo apt-get install gnome-base
```

The 'purge' is important (instead of remove) because it removes config files.

As you can tell I've never had this problem but it's an interesting one so I don't mind looking into it.

---

### Post by Yondergod22 on 2008-06-24
> **molotov00 said:**
> I've been digging around and turned up a few instances of people who ran this:
```
sudo apt-get install ubuntu-desktop
```
They saw the desktop start working again. I'd definitely try that if I were you.

Then I was looking for how people uninstalled gnome. I found that uninstalling ubuntu-desktop does not uninstall gnome, which I was surprised about. To get rid of gnome it looks like you want to remove gnome-base, but it's a bit too early to try that. Do the install first.
```
sudo apt-get purge gnome-base
```

As you can tell I've never had this problem but it's an interesting one so I don't mind looking into it.
ok thanks, ill try to install, and come back and tell you if it works. 
edit: and ill try uninstalling and reinstalling gnome too.

---

### Post by Yondergod22 on 2008-06-24
when I try to install gnome it says it can't be installed and it has unmet dependencies.

---

### Post by molotov00 on 2008-06-24
What is the exact error adn what exactly are you entering? apt-get is smart and tells you it can download the dependencies.

---

### Post by Yondergod22 on 2008-06-24
it says
```
the following packages has unmet dependencies:
  gnome: depends: gnome-desktop-environment (= 1:2.20.2.2)but its not going to be installed
E: broken packages
```
and I tried installing gnome-desktop-environment, and it depends on gnome-keyring-manager, and when I try to install it, it says:
```
package gnome-keyring-manager is not available, but is referred to by another package
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: package gnome-keyring-manager has no installation candidate  
```

---

### Post by molotov00 on 2008-06-24
yeah. Whenever apt-get gives you something like that you can use:
```
sudo apt-get -f install package
```
The -f means 'fix the broken dependencies'. Sometimes you have to go back and forth a bit but if you installed gnome before, it can be installed again.

---

### Post by Yondergod22 on 2008-06-24
I get the same errors as I did without the -f

---

### Post by molotov00 on 2008-06-24
Did you ever add the repositories in sources.list? Or do you have the cd in the drive?

Basically, I can't tell if it's saying it can't find the packages or doesn't want to install them. -f resolves dependencies but if it can't find the packages then you'll need to add the repos. Check this:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

This is really turning out to be harder than it should be... but stick with it. It'll install. Type 'man apt-get' and read about apt-get. Add the repositories and see if you can get gnome installed. I'm off to bed, it's about 4am where I am.

---

### Post by Yondergod22 on 2008-06-24
I have the cd in the drive, and I(think I)added it, by doing ```
sudo apt-cdrom add
```
and I need to go to bed too, its 12:30 here. see you tomorrow...or later today w/e

---

### Post by Yondergod22 on 2008-06-24
was that the right code to add the cd? and I searched for all the errors I got and didn't find anything:(

---

### Post by Yondergod22 on 2008-06-24
anyone have any ideas how to fix this?

---

### Post by Yondergod22 on 2008-06-24
is there any way I could  copy my files onto windows, then reinstall, and copy them back?

---

### Post by Yondergod22 on 2008-06-25
bump

---

