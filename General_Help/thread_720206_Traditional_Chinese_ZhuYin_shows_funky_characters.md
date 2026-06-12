---
title: "Traditional Chinese ZhuYin shows funky characters"
date: 2008-03-10
forum: General Help
---

### Post by nelio2k on 2008-03-10
Hello,

I've been looking around on the forum for a way to get SCIM Traditional Chinese (ZhuYin Big and ZhuYin) to work on Gutsy. 

I followed this guide. I can enter ZhuYin with &#12549;&#12550;&#12551;&#12552;. But the words in the selection box turns out to be squares with letters inside. Such as: &#15585;&#16870;&#20182;&#146893;&#138898;
Some characters show up fine, as seen above, but I have a hard time even inputting simple characters. I can read Chinese perfectly fine on webpages, but rather just have trouble with the input. Could someone help me? 

I can't get a screen shot of the input box, because whenever I press print screen, it dissapears first and then a screenshot is taken.

Thank you!

---

### Post by ilych on 2008-04-02
Bump.

I am having this same problem. I have went through almost all of the SCIM installation guides but all to no avail.

Any suggestions / fixes? Will Hardy address this problem?

Thanks.

---

### Post by ilych on 2008-04-10
Bump.

---

### Post by ilych on 2008-04-11
Bump.

---

### Post by ilych on 2008-04-21
Bump...

I have tried everything in this [Wiki How-To](http://wiki.ubuntu.org.tw/index.php/UbuntuL10n#.E4.B8.AD.E6.96.87.E5.AD.97.E5.9E.8B), but I am see still seeing "funky" boxes instead of traditional Chinese characters, as seen in the attached screenshot.

Any help is GREATLY appreciated.

- Frustrated Ubuntu enthusiast

---

### Post by ilych on 2008-04-22
Bump.
Can someone please help me?
Thanks.

---

### Post by ilych on 2008-04-25
Hardy solved this problem.
Boxes no longer appear.

Remaining problem: when using traditional Chinese in SCIM, simplified Chinese characters still show up
Solution: don't use SCIM, use gcin instead (which now works PERFECTLY in Hardy) :D

Use this wiki to setup gcin: [http://wiki.ubuntu.org.tw/index.php/UbuntuL10n#.E4.B8.AD.E6.96.87.E5.AD.97.E5.9E.8B](http://wiki.ubuntu.org.tw/index.php/UbuntuL10n#.E4.B8.AD.E6.96.87.E5.AD.97.E5.9E.8B)

---

### Post by taiwanjohn on 2008-04-26
I'd like to jump in on this thread, because I'm having similar problems. I had been using scim in Kubuntu with no problems up to Gutsy (7.10) but upgraded to Ubuntu Hardy (8.04) when it came out. Ever since then, my Chinese input has been messed up, almost exactly the way yours was. Except mine had a different font for the first few characters (instead of just "raw-code" characters), as well as having the selection set out of order. Here's an example:

[ATTACH]67346[/ATTACH]

I tried using the /etc/X11/xinit/xinput.d/scim file I'd saved from Gutsy, but didn't help. (The differences between the two files were trivial anyway.) After searching around and trying various ideas, I ran across this thread, and decided to try gcin... 

So far, it seems to be working pretty well, except for one MAJOR problem... I can't select the characters I want. For example, if I type in the zhuyin for "wo", I get this: 

[ATTACH]67351[/ATTACH]

Ok, so far so good... all I have to do now is type "1" and the word "&#25105;" will come out. Right? Wrong! Instead, I get this: 

[ATTACH]67352[/ATTACH]

Hmm... well, what happens if I type [space] instead of "1"? Maybe that's the way... No, that gives me this instead: 

[ATTACH]67353[/ATTACH]

That's nice... but I still can't select anything. 

If I just type "wo" (in zhuyin) and hit ENTER, I get a "&#25105;", but that method only allows me to select #1 from any set.... not much help. 

How is gcin supposed to work? What am I missing here? Any ideas? (How did you get it to work?)

Best, 

--jrd

---

### Post by taiwanjohn on 2008-04-26
Ok, I figured part of it out... 

I found that if you just keep typing, you can keep adding characters to the "buffer" and then "input" whole phrases at a time, instead of one character at a time. But I'm still at the trial-and-error phase, trying to figure out exactly how this works... 

For example, how can I select #2 from this list? (Eg: if I'm writing email to a girl...;-) 

[ATTACH]67358[/ATTACH]

Typing #2 here doesn't have the desired effect. What's the answer? 

Thanks, 

--jrd

---

### Post by taiwanjohn on 2008-04-28
OK, I'm pretty sure I've got it all figured out now. As you probably guessed by now, there's nothing wrong with my gcin installation, that's the way it's SUPPOSED to work. The problem for me was that I didn't understand how it auto-selects and auto-updates characters in the buffer, based on context. 

I asked a Taiwanese friend to try it out, and she said it was working normally. It still seems weird to me, but I reckon I'll get used to it... ;-) 

Thanks again for the tip. 

--jrd

---

