---
title: "Change default position of Chinese language candidate selection bar"
date: 2020-09-14
forum: General Help
---

### Post by makem2 on 2020-09-14
I am using iBUS for Mandarin language in web pages on my XFCE desktop. The web pages are either in Firefox or Chrome.

The candidate selection bar is at the bottom of the web page by default when I type.

Being at the bottom whilst I am typing in the web page address bar is a pain. I would like to have the selection bar in a place more convenient.

I know I can drag the bar to any place but as most of the work I do involves web pages it would be more convenient to lock  it in a location I choose.

Is this possible?

The only options available as far as I can see is to have the bar horizontal or vertical.

---

### Post by dragonfly41 on 2020-09-14
I have only just learned about these ..

[https://beebom.com/google-chrome-flags/](https://beebom.com/google-chrome-flags/)

**but** I don't see them in my Chromium browser.

Something like these might help? Or you might use [X-tile]("https://www.giuspen.com/x-tile/") to position two windows?

**[P.S.]** If in chrome://flags you search "Reader" there are some language accessibility options I see.

---

### Post by makem2 on 2020-09-15
> **dragonfly41 said:**
> I have only just learned about these ..

[https://beebom.com/google-chrome-flags/](https://beebom.com/google-chrome-flags/)

**but** I don't see them in my Chromium browser.


I looked for Google Lens but didn't find it.

> **dragonfly41 said:**
> 
Something like these might help? Or you might use [X-tile]("https://www.giuspen.com/x-tile/") to position two windows?

**[P.S.]** If in chrome://flags you search "Reader" there are some language accessibility options I see.

I will look into your suggestions, thanks.

---

### Post by makem2 on 2020-09-16
Nothing worked there :-(

The popup candidate box appears tied to the bottom left of the current window.

I fail to see why the ability of being able to drag it to a suitable position is of any use when as soon as you type another character it reverts to the bottom of the window. I feel there must be an ability to make it stick via a menu but I cannot find any menu or preferences that offer this.

---

### Post by dragonfly41 on 2020-09-16
I have used AutoKey recently in similar scenarios.
Basically create a phrase which is the URL you would like to type into a field.
Assign some hot key to this phrase.
Place the cursor in the URL field (awaiting the URL to be typed).
Then use methods other than mouse/cursor to get to your language selection bar.
When you hit the assigned hot key your URL will be typed into URLfield.

Another approach is to use Actiona to write a GUI automation script.
This script is run by command .. actexec myscript.ascr

Can you provide an example of a problem page otherwise we are guessing?

---

### Post by makem2 on 2020-09-17
> **dragonfly41 said:**
> I have used AutoKey recently in similar scenarios.
Basically create a phrase which is the URL you would like to type into a field.
Assign some hot key to this phrase.
Place the cursor in the URL field (awaiting the URL to be typed).
Then use methods other than mouse/cursor to get to your language selection bar.
When you hit the assigned hot key your URL will be typed into URLfield.

Another approach is to use Actiona to write a GUI automation script.
This script is run by command .. actexec myscript.ascr

Can you provide an example of a problem page otherwise we are guessing?

I think I may need to explain the input of Mandarin on for example, a web page:

When you being to type the pinyin text for a Mandarin character a small window pops up. In this window are a number of suggestions as to which character you need (predictive characters). In our case we have selected that a choice of 5 characters are shown (can be a larger selection if desired). Each suggestion is given a number 1 > and you select which character you want to be typed on the web page address bar,

For example: 'ni' would produce selections to choose from. If you then type 'hao' and make a choice you would have [FONT=arial]&#22909;. (How are you or hello)
[/FONT]
This is normal when typing Manadarin using a Chinese input such as Sogu. This occurs because Mandarin pinyin has some 5 meanings for each and you need to select the correct meaning.

So, the popup window I am talking about is the 'choices' window and it is needed, not spurious. What I find is a problem is, as I am typing in an address bar near the top of the screen my choice of character appears at the bottom of the screen, some distance away from the cursor I am looking at.

This 'choices' window can be moved around the screen but is never locked where placed. It always defaults to bottom left of the screen for every character choice.

I don't think a screen shot would help (I don't have anywhere to put it) and it is a moving target.

If a Chinese speaker reads this, my apologies if my explanation is not totally correct, but it is the way I as an English speaker, see it.

---

### Post by dragonfly41 on 2020-09-17
I cannot write/speak in Mandarin and I am simply treating this problem as an interesting UI exercise.

I may learn something new as I attempt this.

From your explanation there is a multichoice box offering  5 choices as you type in each character

My confusion is why you need to be typing into the browser url field at the same time as you use the multiple choice box?

Are you typing Mandarin into the top url field and so each character in the url requires reference to 5 choices at the bottom left of the screen? Thus you are hopping around the screen for each character? Is my interpretation correct?


[P.S.] Found this when browsing around to understand the subject.

[http://chinesebrowser.com/](http://chinesebrowser.com/)

---

### Post by makem2 on 2020-09-17
> **dragonfly41 said:**
> I cannot write/speak in Mandarin and I am simply treating this problem as an interesting UI exercise.

I may learn something new as I attempt this.

From your explanation there is a multichoice box offering  5 choices as you type in each character

My confusion is why you need to be typing into the browser url field at the same time as you use the multiple choice box?

Are you typing Mandarin into the top url field and so each character in the url requires reference to 5 choices at the bottom left of the screen? Thus you are hopping around the screen for each character? Is my interpretation correct


[P.S.] Found this when browsing around to understand the subject.

[http://chinesebrowser.com/](http://chinesebrowser.com/)

> **dragonfly41 said:**
> 
Are you typing Mandarin into the top url field and so each character in the url requires reference to 5 choices at the bottom left of the screen? Thus you are hopping around the screen for each character? Is my interpretation correct?



Yes!

Check this out:

[https://www.youtube.com/watch?v=5Ip4VjlD7Ew](https://www.youtube.com/watch?v=5Ip4VjlD7Ew)

The choices which popup below the word 'wo' (me) are the ones to which I refer. Mine popup as I have said, a long way from the cursor.

---

### Post by dragonfly41 on 2020-09-18
In that tutorial link I do not see an example of your "lower left screen drop box with 5 choices".

[Meanwhile read here]("https://askubuntu.com/questions/59356/how-do-i-get-chinese-input-to-work").

[and here (from above thread)]("http://pinyinjoe.com/linux/ubuntu-18-gnome-chinese-setup.htm").

If these threads do not help there are UI manipulation ways of bringing your multi choice box nearer your target data field.
*But that should not be necessary in a well designed UI.*

Also perhaps research Pinyin concordance tools (linguistics tools).

[P.S] Further tips ..

research in google .. "Figma near Pinyin"

and .. "Pinyin NEAR SVG typography"

[https://webdesign.tutsplus.com/articles/the-complete-beginners-guide-to-chinese-fonts--cms-23444](https://webdesign.tutsplus.com/articles/the-complete-beginners-guide-to-chinese-fonts--cms-23444)

---

### Post by makem2 on 2020-09-18
I will read up on those but in the meantime, yes the link does not show the popup going to the bottom, it shows where I would like it to be and where it is when using Windows. However the software they use is not available to me on Linux.

The link was to show you the popup in use only and why it is necessary.

Later I will get to the machine on which the Chinese language is used and will post a screenshot together with the software information in use.

---

### Post by makem2 on 2020-09-18
I will read up on those but in the meantime, yes the link does not show the popup going to the bottom, it shows where I would like it to be. However the software they use is not available to me on Linux.

The link was to show you the popup in use only and why it is necessary.

Later I will get to the machine on which the Chinese language is used and will post a screenshot together with the software information in use.

---

### Post by makem2 on 2020-09-18
> **dragonfly41 said:**
> In that tutorial link I do not see an example of your "lower left screen drop box with 5 choices".

[Meanwhile read here]("https://askubuntu.com/questions/59356/how-do-i-get-chinese-input-to-work").

[and here (from above thread)]("http://pinyinjoe.com/linux/ubuntu-18-gnome-chinese-setup.htm").

If these threads do not help there are UI manipulation ways of bringing your multi choice box nearer your target data field.
*But that should not be necessary in a well designed UI.*

Also perhaps research Pinyin concordance tools (linguistics tools).

[P.S] Further tips ..

research in google .. "Figma near Pinyin"

and .. "Pinyin NEAR SVG typography"

[https://webdesign.tutsplus.com/articles/the-complete-beginners-guide-to-chinese-fonts--cms-23444](https://webdesign.tutsplus.com/articles/the-complete-beginners-guide-to-chinese-fonts--cms-23444)

I have looked at your suggested reading but it relates to fonts and input methods.

I have the correct fonts and input method, I just want to move a window which has focuss to a place on the screen and lock it there until cancelled.

I should have time tomorrow to use the mandarin based computer and will find more detail which may be helpful. I think it is a bug in the  Linux version of the input software and I need to research whether this has been noticed previously.

---

### Post by dragonfly41 on 2020-09-18
> [COLOR=#000000]I have the correct fonts and input method, I just want to move a window which has focuss to a place on the screen and lock it there until cancelled.

One of the first tips posted above was to try X-tile which positions (tiles) multiple windows on your screen. If you produce a **url** which displays your pinyin 5 choice then this method repositioning of windows can be tested. Another tool is xdotool.
sudo apt install xdotool
xdotool --help


[/COLOR]

---

### Post by makem2 on 2020-09-19
> **dragonfly41 said:**
> One of the first tips posted above was to try X-tile which positions (tiles) multiple windows on your screen. If you produce a **url** which displays your pinyin 5 choice then this method repositioning of windows can be tested. Another tool is xdotool.
sudo apt install xdotool
xdotool --help


[/COLOR]

I looked into X-tile and it did not appear suitable. I will check your other suggestion.

I have taken a screenshot showing the choice window in two positions.

1. If a web page is opened for the first time on this machine it defaults to top left of the screen. If the language is set to mandarin then as soon as you type the choices window appears as shown here:

[https://www.dropbox.com/s/xfcdp0djpme7362/1.png?dl=0](https://www.dropbox.com/s/xfcdp0djpme7362/1.png?dl=0)

After entering a space and then typing the next pinyin character the choices window moves to the position shown here:

[https://www.dropbox.com/s/vx6uh2avmpq2u16/2.png?dl=0](https://www.dropbox.com/s/vx6uh2avmpq2u16/2.png?dl=0)

The window will stay in that position, opening and closing as each character is chosen.

2. If a web page is opened for the first time on this machine it defaults to top left of the screen. If the active window is moved or if it loses focus, even if the language is set to mandarin then as soon as you type the choices window appears as shown here:

[https://www.dropbox.com/s/vx6uh2avmpq2u16/2.png?dl=0](https://www.dropbox.com/s/vx6uh2avmpq2u16/2.png?dl=0)

The window will stay in that position, opening and closing as each character is chosen.

3. If a web page is opened for the first time on this machine it defaults to top left of the screen. If the language was english and it is changed to mandarn  then as soon as you type the choices window appears as shown here:

[https://www.dropbox.com/s/vx6uh2avmpq2u16/2.png?dl=0](https://www.dropbox.com/s/vx6uh2avmpq2u16/2.png?dl=0)

The window will stay in that position, opening and closing as each character is chosen.

The ideal input program would be shou xin shu ru fa (Palm input method) but this is not available for Linux. The Chinese user uses Windows 10 so this program is available and preferred.  It's choices window is tied relative to the cursor as far as i can see.

I am trying to wean the Chinese user away from windows especially where more security is needed. If I can get a good input method working well then I will be 99% able to go solely to Linux.

The software being used at the moment is Sogou:

[https://pinyin.sogou.com/linux/?r=pinyin](https://pinyin.sogou.com/linux/?r=pinyin)

The input method used is IBus from a choce of IBus, fcitx and XIM methods.

It occurs to me that I should check which input method is used in shou xin shu ru fa. This may be a little difficult as the machine is set to Chinese but worth a try.

Thank you for your interest @dragonfly41

---

### Post by dragonfly41 on 2020-09-19
Not easy to get a handle on this so I suggest the following:
Run these commands:


```
sudo apt update
sudo apt install xdotool autokey
```


Read here for tips ..
[https://askubuntu.com/questions/53781/application-which-will-display-the-current-coordinates-of-the-mouse-cursor](https://askubuntu.com/questions/53781/application-which-will-display-the-current-coordinates-of-the-mouse-cursor)


```
watch -n 0.1 "xdotool getmouselocation"
```


Run the above command in a small terminal window.


Hover cursor over top url field where you need to type characters.
Take a note of [B]x:nnn y:nnn coordinates.
[/B]

Hover cursor over bottom box where you need to refer to 5 PinYin choices
Take a note of **x:nnn y:nnn** **coordinates**.


Post these **two pairs of coordinate**s (x1:y1, x2:y2) here and I will suggest an [AutoKey]("https://ubuntuforums.org/Root--Software_installation--AutoKey.html") script which hops between top and bottom
 when you press a hot key (I suggest Num+Enter which is at far right of keyboard).


**[P.S.]** I was able to get a better view by opening each image full screen. Dropbox has an overlay box hiding the bottom.

You might also explore Firefox extensions which can reposition popups.

[https://addons.mozilla.org/en-US/firefox/addon/popup-to-tab/](https://addons.mozilla.org/en-US/firefox/addon/popup-to-tab/)

[COLOR=#000000]> Thank you for your interest .. 

I view these as UI juggling problems and often I find myself hopping between windows and menus. But your app should be more consistent in its workflow. Perhaps a word with the developer might bear fruit.[/COLOR]

---

### Post by makem2 on 2020-09-19
Ibus Reference Manual

[https://ibus.github.io/docs/ibus-1.5/index.html](https://ibus.github.io/docs/ibus-1.5/index.html)

I came across this as a way to find how to deal with the wndow position.

---

### Post by dragonfly41 on 2020-09-19
So is it solved?

---

### Post by makem2 on 2020-09-19
> **dragonfly41 said:**
> So is it solved?

No I am afraid not.

I researched Sogou setup and decided to follow fcitx instead of Ibus.

I decided to uninstall both input methods as I saw a suggestion that there could be conflicts.

I have Sogou reinstalled and have used fcitx from the repos, fixing all the missing dependencies.

I now have Chinese input ability but cannot connect Sogou as one of the Chinese options.

I have the choices window in the correct place.

So, have made a step in the right direction. That step will probably make easier passage to a complete solution rather than adding scripts.

Once again thank you for your input, it is much appreciated.

---

### Post by dragonfly41 on 2020-09-19
Sounds a good plan. The Ibus route seems to have had issues with Ubuntu .. [read here]("https://groups.google.com/g/ibus-user/c/HW7qUUF9OGA").

Nothing more I can add.

---

### Post by makem2 on 2020-09-19
```

$ su makem
Password: 
makem@ssdTOSH:/home/han$ sudo apt install fcitc-ui-qimpanel
[sudo] password for makem: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Building dependancy tree
Reading state information... Done
The following packages will be removed
    sogoupinyin
The following NEW packages will be installed
    fcitc-ui-qimpanel

```

REMOVE sogoupinyin!!!!!!

It appears there is a conflict between fcitc-ui-qimpanel and sogoupinyin

I found this when I had fixed sogupinyin which worked correctly and wanted to change the ugly fcitx icon using fcitc-ui-qimpanel:

[https://leimao.github.io/blog/Ubuntu-Gaming-Chinese-Input/](https://leimao.github.io/blog/Ubuntu-Gaming-Chinese-Input/)

Edit:
I tried such suggestions as the link below and something I did appears to have flicked a switch, turning sogoupinyin on in the input management system:

[https://stackoverflow.com/questions/42870024/why-ubuntu-16-04-can-not-input-chinese-characters-using-sogou-pinyin-input-metho](https://stackoverflow.com/questions/42870024/why-ubuntu-16-04-can-not-input-chinese-characters-using-sogou-pinyin-input-metho)

'd' is not missing from the end of my link, it was missing initially.

---

