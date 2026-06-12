---
title: "Removing click action on mouse button UP / 1 click event per mouse button click"
date: 2014-07-29
forum: General Help
---

### Post by Fracta on 2014-07-29
Hi all,

Apologies if this is the wrong section to post this in, please advise if this should be somewhere else.

So I am at work and using copy-paste a lot. I use a combination of the right-click menu and the keys, but it's the rightclick copy menu that is causing me grief.

When I attempt to right click in gedit, the menu will come up and immediately underneath my curser is 'Undo' and because my mouse moves one pixel over onto the menu, I will release the right button and 'Undo' will be activated.

This is more annoying than I can put into words, having huge blocks of text just disappear from simply right clicking. 

I know there are other ways I can copy and paste, but I really just want this work properly.

So instead of having 2 clicks sent, one on mouse down and one on mouse up,

How can I configure this to only send ONE click and ONLY on R mouse down?

Please let me know if you need any info on the OS,

Thanks a lot in advance!

Edit: more info

After looking more extensively I can see other people have not solved this problem:

[http://askubuntu.com/questions/178373/mouse-clicks-when-i-release-the-button](http://askubuntu.com/questions/178373/mouse-clicks-when-i-release-the-button)
[http://askubuntu.com/questions/10586/right-click-menu-on-mouse-release-windows-behavior?rq=1](http://askubuntu.com/questions/10586/right-click-menu-on-mouse-release-windows-behavior?rq=1)
[http://unix.stackexchange.com/questions/33519/how-to-make-x-less-sensitive-when-right-clicking](http://unix.stackexchange.com/questions/33519/how-to-make-x-less-sensitive-when-right-clicking)

I have also figured out that this is almost entirely the fault of gedit. The right click menu is directly under the cursor unlike other programs, so without moving the mouse I can select the first option in the menu. 

Maybe if I could distance the menu from the cursor, or increasing the border size I could solve this issue, but after looking through gconf-editor I don't see a way I can do that.

---

