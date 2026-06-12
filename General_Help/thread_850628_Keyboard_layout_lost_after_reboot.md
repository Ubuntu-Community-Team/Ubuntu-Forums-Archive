---
title: "Keyboard layout lost after reboot"
date: 2008-07-05
forum: General Help
---

### Post by pieroxy on 2008-07-05
I am french and using a french KB. After upgrade to Hardy, the US layout was loaded, so I added the french one and removed the US one.

This worked.

After reboot, the layout is back to US.
To fix it, I need to open the Keyboard panel, go to Layout. Here I see that the french layout is the only one loaded. But still, when I type text, it looks like the US layout is active.

From that point, to get it to work, I just need to add another layout. Any layout. Then it is back working.

What it looks like is that upon boot, it doesn't look at which layout I have and defaults to the US layout. When I open the panel and add a layout, the layouts are taken into consideration.

Any idea ?

My keyboard is a logitech one. I use a KVM from trendnet. Of course, this never happened before...

---

### Post by pieroxy on 2008-07-06
Bump ...

---

### Post by pieroxy on 2008-07-21
Bump again ... This really happens to no one ? Only me ?

Sad story ... ;-)

---

### Post by killerwhale65 on 2008-07-27
I have exactly the same problem with Belgian layout. Seems a bug as no one seems to be able to give a solution.

---

### Post by pgxjon002 on 2008-08-06
hi, i stumbled upon this post quite by chance and recognized the error...  i had the same error in gentoo a while back, with the exception that i use the dvorak-classic layout.  the error appears to be caused by evdev and the xorg-server not playing nicely.  i have not yet found a solution, but i do have a workaround until the naughty children learn to behave.

in a terminal you can change the keyboard layout (in this case to french) with setxkbmap:
```
setxkbmap fr
```

if you need a variant (in my case, the dvorak-classic variant of the us keyboard), you can use:
```
setxkbmap -layout us -variant dvorak-classic
```

of course this is only for one session, so to make it persistent, add the required setxkbmap to the sessions startup:

[INDENT]go to *System->Preferences->Sessions*
in *Sessions*, under the *Start Programs* tab, click on *Add*.
in the *Add* dialog, give it any Name, and put the above setxkbmap command into the *Command* textbox.
then click *OK*.[/INDENT]
next time you log in it will automatically change your map.

like i said its only a workaround until the real issue between xorg-server and evdev gets fixed.

hope it helps

---

### Post by Archimedes0212 on 2008-08-06
I had this problem and found teh way to fix it.

You need to edit your xorg.conf file

First, go to Applications->Other->Keyboard layout  and play around a little to find which layout and variant you need.

Once you know this, it's easy as pie.

Go into xorg.conf and find the Keyboard section.  There will be two Options - one for layout and one for variant.  With the info you gather from playing around - modify the layout and variant to the layout/variant that you need.  Save xorg (and possibly restart) and you're all set and ready to go.

Hope this helps.  If it's not clear just send a message my way and i'll clarify whatever.

Good luck

---

### Post by pgxjon002 on 2008-08-06
i tried that months back when the problem first arose...  it has never worked for me.  even now, my xorg.conf shows "dvorak-classic", but if i dont have my workaround in place, its back to "us".  havent tried it in ubuntu tho.

the only fix (other than the workaround) that has worked has been to fallback to an earlier version of evdev and xorg-server, which is not something i want to do as i run bleeding edge testing versions of everything in gentoo.

---

### Post by gomerbarkley on 2008-08-06
I had this same problem but with dvorak. I tried the method suggested by Archimedes0212 (thanks!), with the following adjustment and had success.
I don't have an Application folder called Other and no Keyboard Layout program. I went to System, Preferences, Keyboard and under the layout tab. So for me the layout is "us" and the variant is "dvorak"
Now, when I edited my xorg.conf (in terminal: sudo gedit /etc/X11/xorg.conf), I had to add the line for variant (there was none) so the whole portion for keyboard was like this:
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbVariant" "dvorak"
EndSection

At first it didn't work because I had used "Dvorak" with a capitol; so you should play around with capitolization it if it doesn't work. Or use pgxjon002's method (setxkbmap -layout us -variant dvorak) to determine correct spelling.

Anyway, now I can reboot and type without mucking about with keyboard preferences as pieroxy described.

---

### Post by Archimedes0212 on 2008-08-07
Yeah, my bad on the GUI location.  I had installed that program separately when I was having this problem.  Glad to hear it worked

---

### Post by oskar.hermansson on 2008-08-08
> **pieroxy said:**
> Bump again ... This really happens to no one ? Only me ?

Sad story ... ;-)

Had the same problem. Changed keyboard settings from us to swedish, but after a reboot, the us layout was back again.

Editing xorg.conf manually worked for me. Changed XkbLayout from "us" to "se", but be aware of the XkbVariant setting . If you are not going to set it to a legal value based on your XkbLayout, you might as well skip the option completely, because keeping it as "alt-intl" makes the keyboard still go us layout... (at least for me)

---

### Post by Elfy on 2008-08-08
It had alos started recently doing it to me for some unapparent reason - editing xorg worked for me

---

