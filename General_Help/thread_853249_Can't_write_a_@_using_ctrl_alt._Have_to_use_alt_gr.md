---
title: "Can't write a @ using ctrl alt. Have to use alt gr."
date: 2008-07-08
forum: General Help
---

### Post by El Chicken DIablo on 2008-07-08
I've got a small problem with both of my ubuntu Hardy Heron 64-bits installations. I can't write the @ symbol like I usually do by pressing ctrl alt and then 2. Instead I have to press alt gr and 2. It's a Norwegian keyboard I'm using, and all the settings are set to Norwegian. On my 64-bits Arch Linux installation I don't have this problem.

---

### Post by El Chicken DIablo on 2008-07-09
Bump.

---

### Post by kristianlm on 2008-09-03
hi!

my first post.


i have the same problem - on all the linux distributions I know, I have to use alt-gr instead of the ctrl-alt combination like I can do on windows.

this is a real pain when it comes to programming code too, symbols like {, [, ], } are very tricky to access (the alt-gr key is hard to hit with your thumb on the move)

does anyone know how to change the keymapping so that ctrl-alt is the same as alt-gr?

thanks!

---

### Post by gewone on 2010-11-10
My question is identical, so I bump instead of creating new thread.
Anyone with a solution? As it's y2k10 and Maverick Meevekat is on the table, there should be one! ;)

Ty in adv~
Regards~

---

### Post by Ancanus on 2010-11-10
There is a good chance that you can tweak this setting at:

System -> Preferences -> Keyboard -> Layouts -> Options...

---

### Post by gewone on 2010-11-11
Can't seem to find it! :/ Am I blind?

---

### Post by morits on 2010-11-17
> There is a good chance that you can tweak this setting at:

System -> Preferences -> Keyboard -> Layouts -> Options... 
I've found the options to map some keys to (3rd level) same as alt gr.
However, the key combination I want is not there "left alt + left ctrl"

Is there a way to add keys/key combinations to the list that is not there already?

---

### Post by gewone on 2010-11-17
Post seems to grasp the concept.
Anyways, something tells me we'll have to suffice without this function-ability! :D

[http://brainstorm.ubuntu.com/idea/15212/](http://brainstorm.ubuntu.com/idea/15212/)

---

### Post by Artorius89 on 2011-08-13
I have filed a report for this bug ([Bug #822872]("https://bugs.launchpad.net/bugs/822872"))  on Launchpad, in which I have tried to explain more extensively this  important problem. There are several help requests such as yours and  mine, around the web, but none of them prompted the developers to solve  the problem. The cause is, in my opinion, lack of mutual understanding  between those, such as us, who daily use an extended keyboard layout  (and so take the importance of this problem for granted), and those who  are not familiar with third level keys (and so see this as a very  marginal or unimportant problem).
We need to get through and prove the importance of this issue, as its  solution would greatly improve usability for European users (as well as  anybody using an extended keyboard layout).
 Please, come over and participate: report that it still affects you, too.
 You will also find (in comment #3) a makeshift workaround that I have devised.
 Thank you very much in advance.

---

### Post by ofnuts on 2011-08-13
> **Artorius89 said:**
> I have filed a report for this bug ([Bug #822872]("https://bugs.launchpad.net/bugs/822872"))  on Launchpad, in which I have tried to explain more extensively this  important problem. There are several help requests such as yours and  mine, around the web, but none of them prompted the developers to solve  the problem. The cause is, in my opinion, lack of mutual understanding  between those, such as us, who daily use an extended keyboard layout  (and so take the importance of this problem for granted), and those who  are not familiar with third level keys (and so see this as a very  marginal or unimportant problem).
We need to get through and prove the importance of this issue, as its  solution would greatly improve usability for European users (as well as  anybody using an extended keyboard layout).
 Please, come over and participate: report that it still affects you, too.
 You will also find (in comment #3) a makeshift workaround that I have devised.
 Thank you very much in advance.

I'm also a European user... for me using AltGr is the "normal" way, even if that means a blister on the side of my right thumb. There are keyboard standards and they are best followed whether we like them or not. Having you own keybaord layout is nice (I wrote a keyboard driver for PC-DOS in the past) but in practice you also get to use other keyboards (other computers, vbox...) that will have the standard layout with AltGr and the brain switch gets difficult.

---

### Post by Artorius89 on 2011-08-13
> **ofnuts said:**
> I'm also a European user... for me using AltGr is the "normal" way, even if that means a blister on the side of my right thumb.
There has been a misunderstanding: using AltGr *is* the normal way, but for third level keys pressed by your *left* hand. On the contrary, using LeftCtrl+LeftAlt is the normal way to choose the third level of keys pressed by the *right* hand. The reason to this is that, according to the rules of good touch typing (that is, to make speedy typing more accurate and comfortable), one hand should press the level chooser (that is, Shift or AltGr/LeftCtrl+LeftAlt) and the other should press the key: the same hand should not have to press both the level chooser and the key, thus stressing the fingers. You can read more in the bug report I have linked to.
 > **ofnuts said:**
> There are keyboard standards and they are best followed whether we like  them or not.
Actually this *is* a standard: a Microsoft Windows one. In Windows, pressing LeftCtrl+LeftAlt+Key gives you the same result as AltGr+Key. Of course, I&#8217;m not saying that Ubuntu should be Windows&#8217;s parrot, but this is a good and essential feature  (for proper and speedy touch typing, at least). No keyboard maker would take away the left Shift key just for the sake of being different.
This has nothing to do with customized keyboard layouts: AltGr would retain its function; it would only be joined by a corresponding left-hand third-level chooser.

---

### Post by ofnuts on 2011-08-13
> **Artorius89 said:**
> There has been a misunderstanding: using AltGr *is* the normal way, but for third level keys pressed by your *left* hand. On the contrary, using LeftCtrl+LeftAlt is the normal way to choose the third level of keys pressed by the *right* hand. The reason to this is that, according to the rules of good touch typing (that is, to make speedy typing more accurate and comfortable), one hand should press the level chooser (that is, Shift or AltGr/LeftCtrl+LeftAlt) and the other should press the key: the same hand should not have to press both the level chooser and the key, thus stressing the fingers. You can read more in the bug report I have linked to.
 
Actually this *is* a standard: a Microsoft Windows one. In Windows, pressing LeftCtrl+LeftAlt+Key gives you the same result as AltGr+Key. Of course, I’m not saying that Ubuntu should be Windows’s parrot, but this is a good and essential feature  (for proper and speedy touch typing, at least). No keyboard maker would take away the left Shift key just for the sake of being different.
This has nothing to do with customized keyboard layouts: AltGr would retain its function; it would only be joined by a corresponding left-hand third-level chooser.

Ah... OK :)

---

### Post by CapsLardmin on 2011-12-25
I'm bumping this thread too because I have the same issue. To me using ctrl and alt is a lot easier to use when typing brackets in programming due to them being awkwardly positioned from altgr. 

When I used ubuntu for the first time I was confused as to why @ didn't work and had to spend a lot of time on figuring out why. Most people assumed I was using altgr so they didn't know what was up. I eventually ended up copying the symbol I needed.

I'm currently a windows user, but I experience this issue in GTK based applications such as pidgin, so maybe this issue should be reported there as well. It wouldn't hurt to get ubuntu as a team to bring up the issue to the GTK team seeing as this issue is still being ignored.

---

### Post by codec_abc on 2012-01-29
I bump this thread too. I wish there is the same shortcut as in Windows. For example, i find to do the "alt gr + -" combination too painful (in order to do the | symbol on European keyboard)

---

### Post by Dingbats on 2012-02-03
Bumping this too.  It's the most annoying thing ever.

---

### Post by nowa on 2012-02-03
When someone writes an paragraph he/she retains the thought of a user in his/her mind that how a user can know it. Thus that’s why this post is perfect. Thanks!

---

### Post by peredur on 2012-02-15
I hate to be a "me too" poster, but...

Me too.  Using [AltGr] just is not acceptable. I'm a programmer and I need easy ways to get to []~{} and so on.

Cheers


PAE

---

### Post by Vaphell on 2012-02-15
not really a solution, i know, but why not have some 'normal' keyboard layout like en-US, where none of programming related characters use ctrl+alt and god-knows-what-else, on switch? Imho the people who designed these localized layouts were retarded.

---

### Post by Leppie on 2012-02-15
> **peredur said:**
> 
Me too.  Using [AltGr] just is not acceptable. I'm a programmer and I need easy ways to get to []~{} and so on.
I do programming as well, and I usually use something like the US keyboard layout for these tasks.
Having said that, why (and how) is [AltGr] more difficult than [left ctrl] + [left alt]? For
[AltGr] + [2] two fingers on different hands are used, whereas [left ctrl] + [left alt] + [2] would use 3 fingers on the same hand to achieve the same.

---

### Post by gewone on 2012-03-11
Awergh, so annoying. I've been checking etcetera Linux forums for a solution on this issue (on a regular basis) for like five years. Now we're running in 2012 and no simple solution available. It sickens me, truly. Guess it's a bit late to bump in with a feature suggestion for the upcoming 'Buntu 12.04 as well.

---

### Post by Obfuscator on 2012-04-15
+1

Look at [https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/822872](https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/822872)

and the upstream bug report at 
[https://bugs.freedesktop.org/show_bug.cgi?id=37232](https://bugs.freedesktop.org/show_bug.cgi?id=37232)

for more discussions. Vote for these and we can make it happen! 

I think it would be better to abolish the "Alt Gr" key and just put a right alt there instead. This way one can type key combinations like Alt+c without looking down. Ctrl+Alt is perfectly fine as third level chooser.

---

### Post by anopows on 2012-06-07
Same problem here. Is there already a fix for this problem?

---

### Post by Jon Hanna on 2012-07-15
Historically, the use of Alt-Ctrl for Alt Gr was due to the fact that many US keyboards do not have an Alt Gr key.
There are two logical explanations for the ANSI-INCITS 154-1988 (R1999) keyboard (the US keyboard).

1. It's designed for writing programs, not human-readable text, since it does so pretty well.
2.  The creators assumed  that Americans are semi-literates that don't use  the full English alphabet when writing such words as naïve or façade  (the same assumption we live with when programs still seem to believe  there are a many languages that can be written in US-ASCII when in fact  there are only a small number of minority languages for which it  suffices, and English isn't one of them).

With either of those assumptions getting rid of AltGr and putting in a second Alt key is a convenience to the user.

Whichever  of these two assumptions was in mind, it turned out that people wanted  to use their computers to write things people could read, and also that  many Americans had better English than the creators of that keyboard.  And that's before we consider those who have other languages. Or indeed  those who write for the New Yorker magazine, whose style-guide for  English requires ä, ë, ï, ö, ü, æ and œ to be heavily used.

Windows  introduced a workaround where Ctrl+Alt was treated as AltGr so that US  keyboards could be used to write human-readable text in languages like  English and Spanish which, what with their being the two most commonly  used languages in the US, was a reasonable user-requirement.

There were two negative side-effects of this:

1.  It made Ctrl-Alt chords for shortcuts a big mess. ("Why does this  application delete the current file every time I type my name?")
2.  Some of us, even outside the US where we had AltGr on just about every  keyboard you'd ever find, got used to the Ctrl-Alt substitute, perhaps  using it in combination with the right-hand letters and numbers or even  favouring it generally (I do).

Now, the best thing to do would be to:

1. Go back in time.
2. Find the people responsible for ANSI-INCITS 154-1988 (R1999).
3. Get a copy of the New Yorker magazine and ask them loudly what country it is printed in until they give an answer.
4.  Bash them repeatedly over the head until they agree to design their  keyboard in such a way that said magazine could be transcribed with it.
5. The whole English-speaking world would grow used to using AltGr as originally intended.

Were I to succeed, I'd still have the habit of using Ctrl+Alt as otherwise there'd be a time-paradox, but it's a sacrifice I'm willing to make. Sadly,  I haven't found a way to implement part 1 of this, as much as I'm  eagerly looking forward to attempting parts 2 through 4. Besides, I'd  have 

So yeah, I'd like the ability to bind Ctrl+Alt to AltGr for compatibility with what I learned when typing on Windows too.

In the meantime, some of you might find the following helps:

1. Go to Keyboard Layout in Systems.
2. Go to options.
3. Open up the "Key to choose 3rd Level" options.
4. Pick a new left-hand AltGr substitute.

It's  no good for me; all the options given either don't exist on my laptop's  keyboard, or are keys where the default uses serve me well (e.g. I'm a  heavy use of Alt to access the menu of whatever app I'm on, of Super to  access the Unity launcher and lenses, etc), but if you won't miss one of  those cases, then you might find this an acceptable workaround.

---

