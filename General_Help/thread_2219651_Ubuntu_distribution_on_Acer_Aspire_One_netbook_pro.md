---
title: "Ubuntu distribution on Acer Aspire One netbook problem"
date: 2014-04-24
forum: General Help
---

### Post by Ray_VK4ZW on 2014-04-24
I have just loaded Ubuntu onto myAcer Aspire One netbook to replace Windows XP.  I find that when I close the cover and then try to awaken the netbook I can not get the screset to open. The screen will show for a second when I move the mouse but the window closes quickly.  I believe that the controls work as I see windos opening if I move and right click the mouse.  The screen remains blank.

I have looked at the "system settings>power"  and have the "whenthe lid is closed" set to "suspend" when the problem occurrs. I now have it set ot "do nothing".  I can't find a setting for hybernate only do nothing or suspend.

Is there anyone who could assist me?

---

### Post by sitro on 2014-04-25
hi,
The english language is not my natural langage and I guess that for many people (not all) on this forum it's the same. So if you can write without mispelled words, it could be more easy to read post. Example, I don't know these words :  screset, windos, whenthe, set ot. 
Even a dictionnary cannot help me because the word one by one doesn't exist. Of course the context of the sentence can help but some time it's not sufficient.
Once this tell, it is just that I am in the process of typing text on my acer Aspire One Netbook first generation with ubuntu 14.04 OS.
After have read your post, I tried check to close the cover of my netbook and after a minute to open it (I should never do that if I didn't read the post):
The power button is blinking yellow. I press the power button then move the mouse, it get back to the login screen in less 5 seconds and the power button become static green. I log in with my password and go back to my session at exactly the same point where I was when I closed the cover.
I tried that previous operation with the 2 options "suspend" or "hibernate" "when laptop lid is closed" in the tab "AC" of "power manager".
For the 2 options, it is working fine.
I didn't check for the tab "on battery" as the battery of my netbook is dead.

---

### Post by sitro on 2014-04-26
Oups, I realise that I made a mistake in my previous post.
The behavior of the screen is just working fine for my external screen plugged to the VGA of the Netbook.
But for screen netbook, it is not working at all.
the netbook screen goes  in black after the login step. and the external screen is in the session.
This behavior is the same for "suspend" and "hibernate"

Nevertheless I can reactivate the laptop screen in the setting of display (don't forget I have an another screen plug on the VGA that is working)  
in settings -> display-> Laptop screen : Check the box "use this output".

---

### Post by trag on 2014-04-26
I dont know what version you have on your machine,but check to see if it supports hibernation [COLOR=#333333][FONT=Arial]Before enabling hibernate, test to see if your computer supports it. To do this, open a terminal and copy/paste the following command:[/FONT][/COLOR]sudo pm-hibernate
[COLOR=#333333][FONT=Arial]Your computer should switch off - turn it back on and all the applications you had open should reopen if hibernate works for your computer.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]**If the above test worked, you can enable hibernate in the Ubuntu power menu by running the following command in a terminal:**
[/FONT][/COLOR]
gksu gedit /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
[COLOR=#333333][FONT=Arial]And in the newly opened file, add the following:[/FONT][/COLOR]
[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
[COLOR=#333333][FONT=Arial]Then save the file.[/FONT][/COLOR]

[COLOR=#333333][FONT=Arial]After logging out and logging back in, "Hibernate" should show up in the power menu.[/FONT][/COLOR]

good luck
Trag

---

