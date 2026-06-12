---
title: "&quot;Record file and application usage&quot; bug?"
date: 2015-04-20
forum: General Help
---

### Post by sanssadness on 2015-04-20
I wanted to make sure the following problem is a bug before filing a bug report. I'm using Ubuntu 14.04 LTS. Basically I noticed that the "Recent" folder under "Places" shows a long history of the files and folders I had recently accessed. I went to System Settings/Security & Privacy/Files and Applications and noticed that my slider for "Record file and application usage" is already set to "Off". To confirm that this was a problem, I clicked "Clear Usage Data...", which instantly got rid of everything in my Recent folder. To me, this confirms that the slider is supposed to do something about this activity not being recorded in the first place, which it doesn't. Am I missing anything?

---

### Post by flaymond on 2015-04-21
I thought it's recorded ***if ***&#8203;you use Dash.

---

### Post by sanssadness on 2015-05-20
Not for me. My history is being recorded even though I accessed the files normally. If I open so much as a text file from a folder, it's recorded. Just open any folder and go to "Recent" on the left. Can anyone else confirm this?

---

### Post by mc4man on 2015-05-20
What I can confirm here is that if "Record file and application usage"  is set to off & all previous is cleared then nothing new is added where it would be expected (nautilus > Recent doesn't show, gedit > prev. list doesn't show, Dash > Home is empty , Dash > Files & Folders > no files, ect.

---

### Post by sanssadness on 2015-05-20
I did some further testing and found that the bug isn't present if I flip the switch to "on," then back to "off" again. No more new activity appears to be recorded. This shouldn't be required, though. I think most people will just set it to "off" one time right after Ubuntu is installed, then never touch it again. Unfortunately, I can't easily reproduce this bug because I upgraded from version 12.04 instead of doing a clean install of 14.04. Can anyone else confirm that the bug exists?

By the way, how would you classify this bug? I went through the bug reporting procedure but it seems to only deal with running programs, and I'm not sure where system settings falls under.

---

### Post by cariboo on 2015-05-21
If you aren't sure what package causes the problem, it is recommended that you file the bug against linux, and let the bug triagers dig through the report to find the cause of the problem. For more info on reporting bugs, see [here]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by mc4man on 2015-05-22
Are saying that you set it to off in 12.04, upgraded to 14.04 & it showed as off but was really on?
If so it may be that after the upgrade your user was given/using  the default (on) but the displaying panel showed (inherited) your previous off setting.
It's possible that there is a difference between how & where for this setting in 12.04 vs. 14.04, ie.  gnome-control-center vs. unity-control-center though the panel itself is provided thru activity-log-manager

---

