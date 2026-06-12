---
title: "Gnome Panel Hangs After Suspend"
date: 2007-10-29
forum: General Help
---

### Post by prince_niceguy on 2007-10-29
I am not sure if this happens to every one. But every time I suspend and come back out of suspend my gnome panel hangs especially the launchers and the application, places and system.

Nautilus no longer works and it also hangs.

I am using 7.10 with compiz.
I have network drives mounted but that should not be a problem.

Has any one got this kind of problem?

---

### Post by cybertesla on 2008-01-12
I have seen this problem also but do not have a solution.  Has anyone figured this out yet?

I have a Compaq Presario V2000 laptop w/ AMD 64bit Turion processor.  The default power management with Gutsy didn't work so changed to uswsusp by doing the following:

sudo apt-get install uswsusp
sudo dpkg-divert --rename --divert /usr/sbin/pmi-disabled /usr/sbin/pmi

This does get suspend working most of the time however hibernate is still broken.  Suspend is 50/50 whether it works when the laptop lid is closed as configured in the Power Management settings.  After coming out of suspend if the gnome-panel is ever clicked then all further mouse clicks are ignored essentially locking the system.  I have gotten around it by ensuring that a terminal window is up before going into suspend.  Then when coming out of suspend I click on the panel to intentionally lock the mouse buttons.  Then I use the keyboard shortcut Ctrl-Tab to switch windows and pull up the terminal window.  For some reason this seems to break the lock.

This is a very cumbersome solution and not acceptable since my wife is the primary user of this machine and has little patience for these types of workarounds.

---

### Post by cybertesla on 2008-01-12
I've done some intense searching and found more on the matter.  I found a long posting the blames this problem on the code that fades the background for the logout screen and suggests using the suspend button or closing the laptop lid as a work around.  This does not work for me.  Even using these methods to get around the fade out, I still get locked up after resume.

I've tried the following workaround without success:

sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start

The one time this did work it locked up again within seconds.

I've also tried...
sudo rm /tmp/.Ice-unix/*

Again, this worked the first time but the next time I click the panel it locked again and there were no more files to delete.

It seems this is a very real problem with gnome-panel that goes beyond the identified fade-out problem.

P.S.  The "Ctrl-Tab" in my previous post should be "Alt-Tab".

---

### Post by prince_niceguy on 2008-01-13
I think it has something to do with nautilus but no confirmation as such... or may be nfs... i have filed a bug but i am not able to generate any crash report.

are you by chance using nfs to mount drives?

---

