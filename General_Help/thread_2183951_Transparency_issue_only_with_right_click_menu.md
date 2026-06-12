---
title: "Transparency issue only with right click menu"
date: 2013-10-27
forum: General Help
---

### Post by Psil0cybin on 2013-10-27
long story short, every piece of transparency works, only problem is when i go to settings and go to Window Manager Tweaksi can change every single thing within the transparency settings and I see it working right away but the only thing that does not change is the option that says'Opacity of popup windows'.I want to change the transparency setting of my right click menu, it seems to be a little transparent but i want to set it more, so i changed that setting and nothing changes.Is there anything i can edit to change this?

---

### Post by Toz on 2013-10-27
What version of Xubuntu/Xfce are you using? It works fine here. Is xfwm4 your active window manager:
```
ps -ef | grep xfwm4
```
...and is xfdesktop managing your desktop:
```
ps -ef | grep xfdesktop
```

---

### Post by Psil0cybin on 2013-10-27
Thank you for your fast replyI have been puzzled about this all day, I spent 3 hours googling with nothing. I have found 2 other people that have had the same issue, they had Ubuntu installed first then installed via xubuntu-desktop

[B][COLOR=#000000][FONT=Ubuntu Mono]ps -ef | grep xfwm4[/FONT][/COLOR]
[/B]```

1000      2120  2109  1 05:27 ?        00:00:23 xfwm4 --display :0.0 --sm-client-id 2e112194e-f4b3-4a0e-8d4c-3351cb79efe71000      2988  2929  0 06:01 pts/0    00:00:00 grep --color=auto xfwm4

```

and

**ps -ef | grep xfdesktop**
```

1000      2140  2109  0 05:27 ?        00:00:00 xfdesktop --display :0.0 --sm-client-id 2ae756072-7fb9-452e-b8ce-c1432a497e801000      3179  2929  0 06:15 pts/0    00:00:00 grep --color=auto xfdesktop

```

It is a wierd problem, right?
and what is even wierder, is the fact that all other transparency options work perfectly!! This is the only one I am having problems with, which leaves me scratching my head...completely confused. The Menu is a SLIGHT bit transparent, but not exactly how much I want it. The Menu when I right click on the desktop is even less transparent, so pretty much only the menus that are viewed over a window are transparent.

I have uploaded a picture here of the menu that does not change
[http://imagebin.org/274922](http://imagebin.org/274922)
 Apicture is worth a thousand words..thanks again for helping me

P.S
I also checked if it was my THEME that was causing the issue, and it is not, i tried using the DEFAULT Xubuntu theme and still the problem persists.

---

### Post by Toz on 2013-10-27
Yes it is wierd. 

Which version of Xubuntu/Xfce?
Have you also installed Ubuntu first then Xfce on top?
Can you try a different Window Manager Style and see if the problem is specific to the style you are using? (potentially related old bug [here]("https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/325662") and similar post [here]("https://bbs.archlinux.org/viewtopic.php?id=123260")).

---

### Post by Psil0cybin on 2013-10-27
> **Toz said:**
> Yes it is wierd. 

Which version of Xubuntu/Xfce?
Have you also installed Ubuntu first then Xfce on top?
Can you try a different Window Manager Style and see if the problem is specific to the style you are using? (potentially related old bug [here]("https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/325662") and similar post [here]("https://bbs.archlinux.org/viewtopic.php?id=123260")).

I am using Ubuntu 12.04 LTS
and Yes I installed Xubuntu after Ubuntu.
but, that should not cause the problem as only xfce processes are running right?
Why would the menu be only slightly transparent, and not let me make it any more or less transparent?
Lots of questions that i cannot figure out

A different windows manager style changes nothing.
seems that the problem is unrelated to themes/styles..once again...odd.

Is there anyway to edit the menu transparency manually via a file?
perhaps something is happening via the GUI? 

I think this is the old bug you are refering to; [https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/325662](https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/325662)
I also looked over that and followed all instructions with no luck at all...it seems like the bug has been persistant only noticed it recently when I made all my settings transparent and wanted to change the menu and noticed nothing works...not matter how much down and up I move the opacity of popup window option..nothing changes
like stated by someone on IRC I think it would be better if No transparency worked, than just this one option.....lol

Thanks you for your quick reply Toz

---

### Post by Toz on 2013-10-27
> **Psil0cybin said:**
> I am using Ubuntu 12.04 LTS
and Yes I installed Xubuntu after Ubuntu.
but, that should not cause the problem as only xfce processes are running right?
Correct.
> Is there anyway to edit the menu transparency manually via a file?
perhaps something is happening via the GUI? 
The file that contains these settings is **~/.config/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml**. You can also use "Settings Manager->Settings Editor" to manage these settings. Look at the xfwm4 channel.

---

