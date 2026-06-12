---
title: "Homemade compiz reload button on top panel Bionic Beaver 18.04"
date: 2018-11-15
forum: General Help
---

### Post by Cavsfan on 2018-11-15
Xubuntu 18.04 Cairo Dock does not come with a composite manager where you can reload compiz or switch window managers.

So, I made one on the top panel that is basically just the startup command but, does function as a compiz reload. 

If you are used to working with Compiz and cannot live without it like many I know, we know it can mess up and needs re-loaded occasionally.

First I created a script called **reload-compiz** in my home directory that contains just this:
```
#!/bin/sh
compiz --replace

```
Then made it executable.

I right clicked on the top panel, moved the mouse down to panel and selected + Add New Items.

Then I selected the top item - Launcher. Clicked add and closed it.

Then I right clicked on the new launcher and selected Properties. Then click the + button on the right and scroll all the way down to Run Program, select that and click Add at the bottom.

In the box that says Launcher at the top click on the bottom right button (edit currently selected item).

It will have something in Command but, ignore that and click on the folder button to the right of Command and maneuver to the script. Make sure the path to the script is in Command.
Name it whatever you want I named it "Compiz Reload". Then on the icon I clicked on that and just selected one of green circles e.g. nm-stage03-connecting03.

Or you can put whatever icon you want, this is Ubuntu, everything is up to you.

Anyway it works for me. Maybe this will help someone else.

It is at the top towards the right where the mouse is.

[[img]http://i.imgur.com/7sPzd3bl.png[/img]](https://imgur.com/7sPzd3b)

---

### Post by NM5TF on 2018-11-15
nice job CavsFan

tommy

---

### Post by Cavsfan on 2018-11-16
Thank you! :D

If you can't find one, make one.

---

### Post by Cavsfan on 2018-11-18
So.... since there is no way to switch window managers either, I made a button for switching to Xfce's default window manager Xfwm4.

I did the same as above just using the command: **/usr/bin/xfwm4 --replace**
Plus I made it a red button just like the green one for Compiz.

I'll remember but, even if I don't I can just hover the mouse over the button and it will tell me what I put in **Name**.

Really starting to like 18.04 and I can see why they say to wait until the 1st point release with an LTS to install it.

Also read where Mark Shuttleworth is extending the life of 18.04 to 10 years, instead of 5 and may do that with 16.04 and 14.04.

---

