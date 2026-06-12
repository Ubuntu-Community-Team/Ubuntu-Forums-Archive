---
title: "Help with GRUB Edit"
date: 2016-01-12
forum: General Help
---

### Post by mlnease on 2016-01-12
Hello,

I'm trying to edit GRUB which 'allows minimal Emacs-type editing'.  Unfortunately, I know nothing about Emacs.  There are a few instructions at the bottom of the page but none for saving edits.  Searching for a 'save edits' command, I found this:  "[Ctrl-x][Ctrl-s]" [here]("http://www.ugrad.cs.ubc.ca/~cs219/CourseNotes/Unix/emacs-startQuit.html"); unfortunately "Ctrl-x" exits the screen immediately without saving.

Any help would be greatly appreciated--thanks in advance.

---

### Post by Seanan on 2016-01-12
Have you tried Ctrl-s?

---

### Post by mlnease on 2016-01-12
> **Seanan said:**
> Have you tried Ctrl-s?

Yes I did, thanks--no effect.

---

### Post by Seanan on 2016-01-12
Try C-x s this will start [SIZE=1]save-some-buffers [SIZE=2]and will ask for input. You will want to input the period key.[/SIZE][/SIZE][SIZE=2][SIZE=1][/SIZE][/SIZE]

---

### Post by mlnease on 2016-01-12
> **Seanan said:**
> Try C-x s this will start [SIZE=1]save-some-buffers [SIZE=2]and will ask for input. You will want to input the period key.[/SIZE][/SIZE]

Hitting C-x *immediately* exits without saving or starting [SIZE=1]save-some-buffers[/SIZE] or anything else.  Thanks again for your time and attention.

---

### Post by Dennis N on 2016-01-12
You pressed 'e to edit' at the GRUB Menu on your screen? That is for one-time temporary changes only - then boot using that change, or go back with ESC. You cannot save those changes.

To change grub menu entries, you have to either:
1) edit  /boot/grub/grub.cfg (changes only kept until next update-grub is run)
2) edit  /etc/default/grub 
3) make a custom menu entry

Above all, you have to know what you are doing. Anything incorrect can prevent booting.

---

### Post by Seanan on 2016-01-12
This was from the GNU Emacs documentation, and it says Ctrl-s works. It also says that Ctrl-c exits but still activates save-some-buffers.

---

### Post by Bashing-om on 2016-01-12
mlnease; Hello;

ninja'd 
Dennis N beat me to it .
+1

[INDENT]inquiring minds want to know
[/INDENT]

---

### Post by Seanan on 2016-01-12
Whoops didn't see your post sorry Dennis.

---

### Post by mlnease on 2016-01-12
> **Dennis N said:**
> You pressed 'e to edit' at the GRUB Menu on your screen? That is for one-time temporary changes only - then boot using that change, or go back with ESC. You cannot save those changes.

To change grub menu entries, you have to either:
1) edit  /boot/grub/grub.cfg (changes only kept until next update-grub is run)
2) edit  /etc/default/grub 
3) make a custom menu entry

Above all, you have to know what you are doing. Anything incorrect can prevent booting.

Thanks for all of this.  I really don't know what I'm doing but received the following advice on another thread:

> When you boot the machine, get to the list of kernels, highlight the first kernel and hit 'e' to edit it.

Look for the line that ends in 'quiet' or 'splash' or both. At the end of that line, add 'nomodeset'. It should look like this:

     Code:
     quiet splash nomodeset 
Follow the instructions at the bottom of the screen to save changes and continue. Any luck? 
Since an update to Wily I've been unable to boot normally; I can only boot by using Recovery mode and manually entering my username and password--even that only works about half the time.

As for your caveat (thanks), I *really* *don't* know what I'm doing. May I ask if the advice above make sense to you (using your instructions)?

---

### Post by Dennis N on 2016-01-12
You can just type in **nomodeset** after the word splash. Then CTRL+X will boot with that change. Again, there is no save and never has been as far as I know. The one time change here is to see if the proposed modification helps. If it doesn't, reboot and you are back to the original menu.

EDIT: If it helps, you can change it more permanently in /etc/default/grub and then sudo update-grub.

---

### Post by mlnease on 2016-01-12
> **Dennis N said:**
> You can just type in **nomodeset** after the word splash. Then CTRL+X will boot with that change. Again, there is no save and never has been as far as I know. The one time change here is to see if the proposed modification helps. If it doesn't, reboot and you are back to the original menu.
OK, got it--*thanks!*  I'll try it again and if that boot works properly, do you suggest I make the change permanent by editing /etc/default/grub?
EDIT
Yep, got it--thanks again.  I'll edit again with my results and hopefully mark SOLVED.
EDIT
I did exactly that--worked like a charm.  Thanks a million everyone.  All hail The Forum!

---

### Post by Bashing-om on 2016-01-12
mlnease; Hey ....

> 
 I really don't know what I'm doing. May I ask if the advice above make sense to you (using your instructions)


only makes sense IF you are having graphics issues . The 'nomodeset' boot parameter disables DKMS forcing the use of the fall back graphic's driver .
In the event of the use of this boot parameter, it is generally expected that once the GUI is activated that a graphic's driver is to be then installed.

'e' key to edit the boot configuration ( add nomodeset ) ; key combo ctl+x to continue the boot process as amended - a one time thing .

"Since an update to Wily I've been unable to boot normally; " Does this imply a broken proprietary graphic's driver in the upgrade process ?

We need to identify the end goal here, then netter advise can be given.

[INDENT][INDENT]all in the process
[INDENT][INDENT][INDENT]holding your mouth right, helps
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Dennis N on 2016-01-12
If you determine it's what you want then: In /etc/default/grub, you would edit the line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and add **nomodeset** after splash for a permanent change (you can change it back later, of course).

Be sure to run sudo update-grub after any change there.

---

### Post by Dennis N on 2016-01-12
And Bashing_om knows more about nomodeset than I do, so take heed.

---

### Post by mlnease on 2016-01-12
Thank you, thank you, thank you.  Problem solved.

---

