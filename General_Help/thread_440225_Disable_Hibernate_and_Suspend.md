---
title: "Disable Hibernate and Suspend"
date: 2007-05-11
forum: General Help
---

### Post by carolinason on 2007-05-11
How or where do you administrate Hibernate and Suspend? 

I need to disable them for a group of users. When I mean disable I mean specifically the options in the quit applet. If totally disabling them will do the trick then that is okay.

---

### Post by carolinason on 2007-06-05
Well I'll answer my own post.

In gconf-editor disable the keys by unchecking :
/apps/gnome-power-manager/can_hibernate 
and
/apps/gnome-power-manager/can_suspend

Right click on these keys and set as mandatory.

Thanks, I'll back with me after more me!

---

### Post by zzztownsend on 2007-06-18
Just so you don't feel lonely with this post - it helped me out!
Keep up the bizarre conversations with yourself!!!

Matt

---

### Post by vanadium on 2007-06-18
Indeed, don feel too lonely! This is helpful to other people. Don dispair. Next time, someone else might actually be faster than you in finding the solution. ;)

---

### Post by johnross@johnross.com on 2007-11-07
I had problems with a couple of my old machines resuming from suspend/hibernate. I couldn't seem to fix that so I just disabled the functions by editing /etc/default/acpi-support and commenting out the lines for ACPI_SLEEP and ACPI_HIBERNATE per the instructions in the file. After restart there are no more menus for either function.

Hope that helps!

---

### Post by J0hnn1ewalker on 2007-12-02
Whilst looking for a solution myself I found this:

[http://jeremy.visser.name/2007/02/how-to-disable-suspend-and-hibernate-for-all-users-in-ubuntu](http://jeremy.visser.name/2007/02/how-to-disable-suspend-and-hibernate-for-all-users-in-ubuntu)

As a complete noob to all things Linux this seemed very simple, hope this helps others.

Just in case the link gets moved broken:

Step One

Press Alt+F2. A dialog box will come up entitled &#8216;Run Application&#8217;. In the text entry field, type:

gksu gconf-editor

&#8230;and click &#8216;Run&#8217;. You may be prompted with your password, in which case, enter your password.
Step Two

An application named &#8216;Configuration Editor&#8217; will come up. This program is for editing fine-grained details about your desktop. GNOME contains a database for storing your preferences called &#8216;gconf&#8217;. Configuration Editor is an application which edits the gconf database. Windows users may be familiar with the registry, which is a similar database.

In the Configuration Editor, navigate through the tree (located on the left-hand pane in the window) to:

/ &#8594; apps &#8594; gnome-power-manager
Step Three

In the right-hand pane, a new set of &#8216;keys&#8217; have appeared. These keys are specific to the gnome-power-manager, which you selected in the previous step. Find the keys named &#8216;can_hibernate&#8217; and &#8216;can_suspend&#8217;. Uncheck them both.

In Ubuntu version 6.06, the &#8216;can_suspend&#8217; key is already unchecked. This is normal.
Step Four

Now, right-click on &#8216;can_hibernate&#8217;. From the context menu, choose Set as Mandatory. No dialog box will come up confirming that it worked, but I promise, it worked!

Do the same for &#8216;can_suspend&#8217;. Now, close the Configuration Editor.
Step Five

Log out of your system (From the System menu, choose Quit, then choose Log Out). Now log back in. You should now see that when you go to the Quit menu, the Suspend and Hibernate buttons are gone.

---

### Post by Jeremy23 on 2008-01-15
> **J0hnn1ewalker said:**
> Just in case the link gets moved broken:

I try *very* hard to make sure I don't break incoming links. :) If I ever change URLs, or domain names, I'll be sure to create a 301 redirect.

---

### Post by mkoyle on 2008-05-07
In Hardy, this seems to have moved just slightly.  The keys are now

/apps/gnome-power-manager/general/can_suspend
/apps/gnome-power-manager/general/can_hibernate

--Matthew

---

### Post by BlueSkyNIS on 2008-05-13
> **mkoyle said:**
> In Hardy, this seems to have moved just slightly.  The keys are now

/apps/gnome-power-manager/general/can_suspend
/apps/gnome-power-manager/general/can_hibernate

--Matthew

Yes, that helped :)

---

