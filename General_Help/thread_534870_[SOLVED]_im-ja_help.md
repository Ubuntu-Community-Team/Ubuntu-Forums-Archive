---
title: "[SOLVED] im-ja help"
date: 2007-08-25
forum: General Help
---

### Post by dmitric300 on 2007-08-25
I recently installed ubuntu 7.04 in a dual boot setup with Windows XP on a 2Ghz P4 PC and I'm now trying to get a Japanese IME to work with Open Office and firefox (something similar to the one microsoft offers for office). I installed im-ja ([http://im-ja.sourceforge.net/](http://im-ja.sourceforge.net/) ) and it works for gedit but at present I can't get it to work with anything else. 

If anyone has any experience with im-ja, any advice would be much appreciated.

---

### Post by ddrichardson on 2007-08-26
I use scim - set it up through the languages option under settings.

---

### Post by chilker on 2007-08-27
for some bizarre reason, I have been unable to get SCIM to convert Japanese hiragana into Kanji. It's bizarre. But with im-ja, I can get Kanji. However, it seems to only work in gaim and gedit, and probably some other stuff I haven't yet tried out. I'll fiddle with it, but I'm not sure what I can do. I'm still pretty new with Linux... well, two years, actually, but I haven't done a ton with it, I've just customized somethings and stuff. I'm still pretty novice.

---

### Post by ddrichardson on 2007-08-27
I'm not sure what I'm doing differently but I'm not having any trouble with Anthy as an IME - its giving me kanji from hirigana when I hit space in gedit, openoffice - infact everything I tried.

All I did was add Japanese support from the Administration/Languages. Then choose Japanese/Anthy from the scim menu.

---

### Post by chilker on 2007-08-27
Lo and behold! I just figured it out! This was so random! I hope this can help anyone forever! With im-ja, to type in any program (well... I've only tried firefox and open office) Go into a saving window (for firefox, there's "save page" in the file menu and in open office, act like you're about to save a document, even with nothing on it) then in the little field that is empty, where you would type your document's name, right-click and go down to Input Methods and Choose Japanese. with that, you should be able to type &#26085;&#26412;&#35486; *anywhere* on that program, as long as it's open. You may have to do this every time you open the program (hopefully there's a workaround i haven't yet figured out) but it works! I can now type in any other field. I'm so excited!

---

### Post by ddrichardson on 2007-08-28
Great - can you mark this thread as solved?

---

### Post by dmitric300 on 2007-08-28
Thanks a lot, although it isn't a solution, a work around is still nice. Kudos to you.

---

### Post by ddrichardson on 2007-08-28
I might do a quick expansion on input methods in the documentation and the wiki - I thought they were covered, purely because I'd never seen any complaints. Perhaps this is something we've overlooked because of the cross over with translations.

---

### Post by soldave on 2007-09-02
This is my first post on the forums as I've just installed Ubunt today, and it's partly to congratulate chilker on finding a workaround for this problem.  I am having a similar problem in that I can view Japanese text on websites and such, but wasn't able to type it.

The input method seems to default to uim, which I can't get to display Japanese.  Using this workaround, I can select the Anthy Japanese set and use my Japanese keyboard like I would in Windows.  Does anyone know how to fix this so that you don't have to try and save a file whenever you want to type in Japanese?

---

### Post by chilker on 2007-11-04
Sorry, I couldn't find another workaround... but now that I've upgraded to Gutsy, I've found things working a lot better.&#12383;&#12392;&#12360;&#12400;&#65292;&#20170;SCIM&#12391;&#26360;&#12369;&#12427;!&#12393;&#12371;&#12391;&#12418;&#26360;&#12369;&#12427;&#12290;Firefox&#12418;gedit&#12418;&#20309;&#12391;&#12418;&#12356;&#12356;&#12391;&#12377;&#12290;It's excellent. I don't have to do any strange workarounds. I hope you've upgraded to Gutsy, and it works out for you too.
Good luck,
Chilker
Oh, and thanks for the congratulations, haha, it was just kind of a mishap. But it worked :)

---

### Post by Angus77 on 2007-11-11
This is crazy! I have it exactly the other way around.

It was no effort at all for me to get Anthy working in Feisty, but now that I've upgraded, I'm having to use chilker's workaround.

Sure glad I found this thread!

---

### Post by Jakevn on 2008-01-29
I had this issue too but got sick of opening the save dialogue every time I wanted to use Anthy.

 First off, for those starting from the beginning, make sure you go to System > Administration > Language Support and check the box to the right of Japanese. (You may have to scroll to the right to see the checkbox)

 It should automatically download the correct packages necessary for the next step, but if you would like to double check, go to System > Administration > Synaptic Package Manager and do a search for scim. Scroll down and make sure scim and scim-anthy are installed. 

To remedy the input selection issue, go to terminal and type this:

```
sudo gedit /etc/X11/xinit/xinput.d/scim
```

Hit enter, input your password, hit enter again and it will bring up the SCIM config file.

Look for the following line:

```
GTK_IM_MODULE=xim
```

And change it to this:

```
GTK_IM_MODULE="scim"
```

*[Note: If you would like to use scim for KDE programs as well, I believe you will need to change the line QT_IM_MODULE.]*

Save the file and then restart.

So you don't need to click the toolbar every time you switch, make sure you go to System > Preferences > SCIM Input Method Setup. Click on Anthy under the IMEngine dropdown and go to the Key Bindings tab. Click Toggle On/Off and then click Choose Keys on the bottom right. Delete all current key bindings and replace with your own preference (I chose alt + tilde since that is what Windows uses). Be sure to click Add after you select which keys you will use and then click OK.

 If you wish to switch between Hiragana, Katakana, Romaji, etc. you can use the Function keys AFTER you type the word you want to change.
F7 = Full width Katakana.
F8 = Half width Katakana.
F9 = Full width Romaji.
F10 = Half width Romaji.

You can select which kana you wish to be considered for kanji conversion by using shift + left/right arrow.

---

