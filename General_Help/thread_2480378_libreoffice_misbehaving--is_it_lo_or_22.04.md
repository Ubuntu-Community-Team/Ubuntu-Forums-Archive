---
title: "libreoffice misbehaving--is it lo or 22.04"
date: 2022-10-27
forum: General Help
---

### Post by dgermann on 2022-10-27
Friends--

Since upgrading to 22.04 LTS, libreoffice has been acting strangely. This is on three computers. One I did a fresh install of 22.04, two simply did upgrades from 18.04. I currently have lo version 7.3.6.2.

Here are some of the things going on (there are others):
1. From within lo, I cannot use ctl-click to open multiple files. (I can however use shift-click to open several files if they happen to be next to each other in the file list.)
2. Files do not open to the last saved place. (Yes, I have all my info filled in under Tools > Options > LO > User Data)
3. It takes 7 to 10 seconds for the font name menu box to open.
4. The key combo I have set (ctl-sh-end) to select to document end sometimes works, mostly does not. Have similar problems with other key combos.

These problems are new to me--we did not have these issues in the prior version I was using under 18.04.

Here is what I have done to trouble shoot:
[LIST]
[*]On one computer, I used synaptic and re-installed lo.
[*]On the same computer, I removed and then re-installed lo.
[*]On a second computer, I tried renaming my user profile and letting lo create a new one, following [https://wiki.documentfoundation.org/UserProfile#Resolving_corruption]("https://wiki.documentfoundation.org/UserProfile#Resolving_corruption")
[*]On the second computer, I tried removing lo entirely and installing from the lo Website (7.3.6.2)
[*]On the second computer I purged 7.3.6.2, and installed instead 7.1.8.1
[/LIST]

Only the last made any difference: it does seem to work to select from the current cursor position up a page or down a page, but no ctl-sh-end, and I think it opened the font name box quickly. But the other problems remain.

What can I do to get lo to behave?

Thanks!

---

### Post by dgermann on 2022-11-02
Anybody have any ideas where I can turn?

Thanks!

---

### Post by Hagar Delest on 2022-11-12
Rather weird for most of your issues.
I tested on 7.2 and 7.4 and it works fine for the multi selection to open files (xubuntu 22.10, ubuntu packaged version for 7.4). What I discovered however is that in 7.4, the open/save dialog option is now hidden in the advanced configuration (what's the point???) and anyway it doesn't work, I only get the LO dialogs, whatever the entry UseSystemFileDialog is (false or true, but I use the VCL_PLUGIN = GEN option, it may be the issue).
The basic cure is indeed to reset the profile. If no change, that's more strange. Try may to install through Flatpak or Appimage. Flatpak should provide a better system integration.

The position of the cursor is a known issue. It has been broken at some point, even if some LO developers don't want to recognize that.
With the help of the AOO/LO forum, a macro has been made to workaround that: [Automatically setting bookmarks with strictly formatted names]("https://forum.openoffice.org/en/forum/viewtopic.php?t=108684"). My version is the last one, more basic. I have a custom toolbar with a button to trigger the save position and another to go to the last save position. See if that helps.

---

### Post by dgermann on 2022-11-13
Hagar--

Thanks for jumping in here. I recognize your name: you have helped me in the past. I have visited the thread you linked, and posted a follow up question there.

I will play with flatpak on a machine where lo is a less vital to what I am doing day to day, and report back.

Since your versions are not giving you similar troubles, I have to think it is not LO that is the problem, but perhaps my install of ubuntu 22.04, or possibly operator error. But then again, I installed one computer from scratch, and two by upgrade (each was from 18.04 to 20.04 to 22.04). All three machines have luks/lvm, if that is a clue.

Today I noticed that on one machine select to end of document sometimes works on one document, and sometimes not on the same document!

Thanks, Hagar!

---

### Post by Hagar Delest on 2022-11-16
> **dgermann said:**
> Today I noticed that on one machine select to end of document sometimes works on one document, and sometimes not on the same document!

I have seen something similar: on old documents opened by LO, it goes straight to the last cursor position as intended. However, as soon as I save the file with a newer version, then the position is lost. So it's a problem with the metadata update.

See also the related bug report: [Bug 140147 - position of cursor not saved]("https://bugs.documentfoundation.org/show_bug.cgi?id=140147").

---

### Post by dgermann on 2022-11-16
Hagar--

Well, the bug makes it look like there will not be a fix soon. Thanks for pointing out the bug report. I will just use bookmarks to find my place, especially in large docs. At least I do not have to keep chasing this, thinking I am going crazy!

The metadata update--is that something I as a mere user have any control over?

Thanks very much, Hagar!

---

### Post by Hagar Delest on 2022-11-16
Not sure if a macro could do that. I know that with a macro you can change the template on which a file is based for example. So maybe the cursor position can be stored the same way. I've not checked how that cursor position was recorded.
I stuck to a version that kept that feature working and recently decided to upgrade because anyway I had to click at each document opening: almost always, the headers were active as if the cursor was in the header. And it slows significantly the application. Thus, if I had to click anyway, then just click a button that does something useful. The macro posted in the forum was the trigger, I adapted it to my need (more basic than the first version proposed in the forum).

---

### Post by dgermann on 2022-11-16
Hagar--

When you say you click on the header, does that mean one of the icons like indent or spell check, or a header style in the body of the document? Or something else?

You also said you kept to a version where that feature still worked. I am thinking of going back to whatever was working for me in Ubuntu 18.04 or 20.04. What version of LO worked for you before you went to 7.1?

Thanks, Hagar!

---

### Post by Hagar Delest on 2022-11-17
I mean that the document opens with the cursor in the header at the top of the page. That selects all the headers at once. When they are active, try to scroll you will notice that the speed is significantly reduced compared to the case where the cursor is in the main text instead:
[ATTACH=CONFIG]291257[/ATTACH]

The last version that did work with the cursor position was 7.2. And before, it may have been 7.0, not quite sure.
I'm glad I'm not alone missing this feature so much. This need was quite dismissed by some LO devs.

---

### Post by dgermann on 2022-11-17
Hagar--

OK, now I know to what you were referring.

Just checked this site [https://www.debugpoint.com/libreoffice-upgrade-update-latest/]("https://www.debugpoint.com/libreoffice-upgrade-update-latest/") and they say Ubuntu 20.04 had LO 6.4.7, and 18.04 had 6.2. So if 7.2 does not resolve most of these issues, I might just fall back to one of those, where things were working better.

The cursor placement is a middle level irritation at the moment. The bigger one is not being able to open several files at once. And not reliably highlighting to the end of the document or page. I have just been using cursor placement as a proxy for the whole set of issues.

(On my 714 page document I tried re-saving the document, then tried to create a blank document and paste the contents into the new clean document: neither worked to find the cursor placement.)

Thanks, Hagar!

---

### Post by dgermann on 2022-11-17
Hagar--

Report:

On one of my test machine (called yarn), I installed flatpak and the LO version (7.4.2.3) they provide. Here are the results from a three page document, all text:

1. ctl-alt-up (and down) did not work: they did nothing, cursor just sat there
2. ctl-sh-end did not work: did nothing, cursor just sat there
3. open multiple documents did not work
4. save cursor position did not work: came back to random positions, sometimes to the first page. Same result if I simply closed and reopened the document or closed and reopened LO.

Alongside this on the same machine I had previously installed LO 7.1.8.1. I ran the same tests with it and got the same results.

---

### Post by Hagar Delest on 2022-11-18
Strange. It works fine on my xubuntu (22.10) machine with LO 7.4.2.3 from the ubuntu repositories (except last position of course).
I thought there would be more answers in the ubuntu forum. You can try to post in the GNU/Linux section of the AOO forum about the shortcuts issue, there are ubuntu users.

---

