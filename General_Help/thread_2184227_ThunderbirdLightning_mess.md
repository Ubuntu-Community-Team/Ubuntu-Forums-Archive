---
title: "Thunderbird/Lightning mess"
date: 2013-10-28
forum: General Help
---

### Post by DrScum on 2013-10-28
Ubuntu 12.04 LTS, I am using Thunderbird in combination with lightning. A regular update through the update manager installed lightning 2.6.1 which is incompatible with thunderbird 24.0 the version in the ubuntu repos. In order to get my calendars and task lists back, I had to install Thunderbird 24.0.1 from the mozilla repos. I do have my calendars and tasks back now but the Thunderbird main window is randomly loosing its window decorations. I have seen this behaviour with Firefox too on occasions, but with Thunderbird now the frequency is not tolerable. 

Does anyone have an Idea how I could fix this?

I guess I should mention that I am using the Gnome fallback version of the desktop along with compiz.

---

### Post by vanadium on 2013-10-28
The (far)easier approach is not to update thunderbird, but to remove lightning 2.6.1, and install 2.6.0 again. You will find 2.6 here: [https://addons.mozilla.org/en-US/thunderbird/addon/lightning/versions/](https://addons.mozilla.org/en-US/thunderbird/addon/lightning/versions/) Download it, then drag it onto thunderbird to have it installed.

Next, you want to turn off automatic updates of addons: Edit - Preferences - Advanced, Update tab. Otherwise, the offending version will be there again in a few days.

Once thunderbird 24.0.1 is pushed on our systems, we will need to upgrade Lighting to 2.6.1. It may then again be safe again to automatically update the plugins: this is supposed to be a one time hick up.

---

### Post by DrScum on 2013-10-28
Well, I already went down the updating Thunderbird road and won't go back now.
I am far more interested in finding a solution for the mozilla products constantly loosing the window borders (close, minimize bttons and so on).

---

### Post by vanadium on 2013-10-28
The chance of that happening with the version in the repositories might be less than with versions you obtain from elsewhere. That is why I suggested to stay with the default version of Ubuntu. With the Ubuntu version, a "thunderbird-gnome-support" package is installed as well. Maybe that makes the difference.

---

### Post by rvboutin on 2013-10-28
Hi,
I can confirm that Lightning 2.6.1 causes the calendar to be greyed out/unavailable with Thunderbird 24. The work around I found here ([http://www.linuxquestions.org/questions/linux-software-2/thunderbird-calendar-completely-greyed-out-4175482276/](http://www.linuxquestions.org/questions/linux-software-2/thunderbird-calendar-completely-greyed-out-4175482276/)) is to uninstall Lightning 2.6.1 and downgrade to Lightning 2.6.
Rv

---

### Post by pvandoren on 2013-10-28
I had the same issues:  I followed the instructions on: [http://linuxg.net/how-to-install-thunderbird-24-0-1-on-ubuntu-13-10-13-04-12-10-12-04-linux-mint-16-15-14-13-elementary-os-0-2-and-pear-os-8/](http://linuxg.net/how-to-install-thunderbird-24-0-1-on-ubuntu-13-10-13-04-12-10-12-04-linux-mint-16-15-14-13-elementary-os-0-2-and-pear-os-8/)
and lightning worked again.

I agree, staying with the standard repos is better, but on a 64-bit system the standard repo didn't support lightning (at least when I installed it), so that's probably the root of our problems.  But this updated repo got me updated to 24.0.1 and my calendar works again. 

Pete

---

### Post by hendrik-0 on 2013-10-28
does anybody know when thunderbird 24.01 will become the regular version thunderbird version for ubuntu, i.e. will be added to the software center?

---

### Post by ray_field2 on 2013-11-02
> **DrScum said:**
> Well, I already went down the updating Thunderbird road and won't go back now.
I am far more interested in finding a solution for the mozilla products constantly loosing the window borders (close, minimize bttons and so on).

I am now having the same problem: only window controls are close and minimize, and nothing is up on the Unity status bar. did you come across a fix?

I guess there's a chance maybe the latest T-bird update will fix things, but having struggled with the Lightning issue I'm not at all confident about proceeding with it.

---

### Post by ray_field2 on 2013-11-02
just uninstalled Lightning and allowed software updater to install latest Thunderbird, then went to add-ons and put in Lightning (now 2.6.2) & everything (window controls, Lightning) seems ok now.

---

### Post by billcauley2 on 2013-11-02
Confirm.  Thunderbird 24.1.0 and Lightning 2.6.2. work.  A change was that you have to enter "location" in Lightning, since it doesn't pick up the system default as before.  Also, there is no longer a calendar in the 'Events' column.

---

