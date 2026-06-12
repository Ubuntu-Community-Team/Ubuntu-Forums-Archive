---
title: "Text Entry In Terminal Problem"
date: 2013-10-20
forum: General Help
---

### Post by Wheel on 2013-10-20
I'm not sure if this qualifies as a bug.  If it does, could you please advise me as to how to properly report this as such.

I'm dual booting Win 7 and Ubuntu on my desktop PC.
I have just clean installed Saucy.

I was using Terminal to edit the grub config file to alter boot order to my preference.

I entered "sudo gedit /etc/default/grub".
Terminal announced: "~/.config/ibus/bus not owned by root", but gedit opened the grub config file anyway and allowed my edits.

This error message seemed like it might be important.  Why else would this be reported to me?
So I used chown to transfer ownership of the file to root.
A re-try of the command executed smoothly with no complaint from the Terminal.

After a subsequent shut down & start up, I opened Terminal but discovered once again that I could not enter any text.
I was also denied text entry in gedit docs, writer docs, as well as the search query box on Firefox.
I ***was*** able to enter text into HUD and Dash.

Eventually, in Terminal, I fgured out that if I changed the input from ibus to simple (or none), I was able to enter text.  But this was a session-only temporary fix; next time into the Terminal, text entry was denied again.

I finally chown the bus file back to "me" and text entry problems disappeared.

Is this anything I need to worry about?
Is there any problem in leaving "me" as the owner of this file/folder?


(I do remember seeing, during Saucy install, a message balloon about ibus having changed, but I paid it little attention.  I'm not sure if this has any bearing on this problem as I'm not skilled enough to appreciate the value of any such change.)

---

### Post by JKyleOKC on 2013-10-20
> **Wheel said:**
> I entered "sudo gedit /etc/default/grub".
Terminal announced: "~/.config/ibus/bus not owned by root", but gedit opened the grub config file anyway and allowed my edits.

This error message seemed like it might be important.  Why else would this be reported to me?
So I used chown to transfer ownership of the file to root.
A re-try of the command executed smoothly with no complaint from the Terminal.

After a subsequent shut down & start up, I opened Terminal but discovered once again that I could not enter any text.
I was also denied text entry in gedit docs, writer docs, as well as the search query box on Firefox.
I ***was*** able to enter text into HUD and Dash.

Eventually, in Terminal, I fgured out that if I changed the input from ibus to simple (or none), I was able to enter text.  But this was a session-only temporary fix; next time into the Terminal, text entry was denied again.

I finally chown the bus file back to "me" and text entry problems disappeared.

Is this anything I need to worry about?
Is there any problem in leaving "me" as the owner of this file/folder?The original message that roused your interest really need not have been displayed at all, since the situation it reported had no effect at all on your ability to do the original editing.

All files in the "~" directory, with very few exceptions, are normally owned by you, not root, so the original ownership was correct. Changing it to "root" is what caused the inability to enter text in those areas you list, and changing it back restored normal operation. There's no need to worry about it, and leaving yourself as the owner is the correct course of action.

If there's any bug to report, it should be against the area of "ibus" that issued the original confusing message!

---

### Post by Wheel on 2013-10-21
> **JKyleOKC said:**
> The original message that roused your interest really need not have been displayed at all, since the situation it reported had no effect at all on your ability to do the original editing.

All files in the "~" directory, with very few exceptions, are normally owned by you, not root, so the original ownership was correct. Changing it to "root" is what caused the inability to enter text in those areas you list, and changing it back restored normal operation. There's no need to worry about it, and leaving yourself as the owner is the correct course of action.

If there's any bug to report, it should be against the area of "ibus" that issued the original confusing message!

Thanks for that.

I was fairly cetain that owning the files in my own home folder made sense, but everything doesn't always make sense.
Especially in the early days of any new flavor of Ubuntu.

---

