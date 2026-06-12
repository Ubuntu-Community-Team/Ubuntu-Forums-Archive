---
title: "Where's Japanese in SCIM?"
date: 2007-10-25
forum: General Help
---

### Post by NFITC1 on 2007-10-25
I've searched this forum several times and can't figure out what I'm doing wrong.
I'm using Gutsy and I need Japanese input. I uninstalled and reinstalled SCIM and unselected and reselected Japanese language support and keyboard layouts (rebooting after each step). However, Japanese doesn't appear as an option in my SCIM menus. What am I missing here?

---

### Post by hrod beraht on 2007-10-25
Did you add the UIM Applet to the panel? (Right click on the panel> Add to panel...).

To try out inputting Japanese, launch a text editor, such as Gedit. Click on the input mode selector in the UIM applet and select Anthy. By default you should still be in direct input mode under Anthy and typing will produce English characters. Hit shift-space to toggle into Japanese input mode. If the UIM Applet input mode logo does not say &#12354;, indicating hiragana mode, either click on the applet and select hiragana mode.

Bob

---

### Post by NFITC1 on 2007-10-25
UIM Applet isn't an option. How do I get it other than apt-get install uim?

---

### Post by NFITC1 on 2007-10-26
Well, I got uim applet in the panel, but it's not letting me switch to Japanese. I know I selected the language support (as mentioned in the first post), so why are none of my language applets acknowledging it's there? I'd still prefer to have SCIM running since that's what I've been using. UIM seems to have more options, but looks more confusing. I really just want ONE of them to work.

---

### Post by gonta on 2007-10-27
This one frustrated me for a while too. SCIM  is configured but probably isn't launching hence nothing on the toolbar to click on.

To see if it will launch OK

ALT +F2
type scim -d

You should see the notification icon on your toolbar.

To make it always launch

Go to System -> Preferences ->Sessions - Startup Programs tab
Click on Add
In the Edit Startup Programs box put 
Name = SCIM
Command = scim -d

Restart your system.

---

### Post by NFITC1 on 2007-10-27
> **gonta said:**
> This one frustrated me for a while too. SCIM  is configured but probably isn't launching hence nothing on the toolbar to click on.

To see if it will launch OK

ALT +F2
type scim -d

You should see the notification icon on your toolbar.

To make it always launch

Go to System -> Preferences ->Sessions - Startup Programs tab
Click on Add
In the Edit Startup Programs box put 
Name = SCIM
Command = scim -d

Restart your system.

I did all this a day or two ago to no avail.
I got it to finally work, but I don't want to mark this as solved. I am not really sure what happened. I did a complete reinstall for probably the third time and it just started working like it has always done. &#35501;&#12417;&#12426;&#12414;&#12377;&#12363;&#12539;Even within the same post. Yay that I got it to work, but I'm not sure how.

---

