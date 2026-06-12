---
title: "wtf just happened??"
date: 2007-07-28
forum: General Help
---

### Post by Chymera on 2007-07-28
ok, ive just about had it with ubuntu; i can live with the fact that 5.1 doesnt work, i can live with the fact that ive wasted about 15 dvds because gnomebaker graveman and xfburn suck, i can live with the fact that it takes about 2 weeks to set up everything you want, i can live with the fact that WinE sucks and cant get 4-year old games to work (even though on the official website it says they work), and so on...

BUT CAN ANYBODY TELL ME WHY THE HELL, after i rebooted in windows so i could get some stuff done in cs3, THE UBUNTU HAS JAMMED! it takes about 2 minutes to load the desktop (ie. i get a very basic desktop after logon and then after 2 minutes all the stuff that should run on startup appears), and it dosnt mount my 2 ntfs partitions. WTF? you ppl call windows unreliable? SEEING AS WITHOUT EVEN ONE ERROR MESSAGE TO TELL ME WHAT HAPPEND THIS OS GOES "PUFF"?

---

### Post by kostkon on 2007-07-28
I understand that you are upset, but you don't need to e-shout...

Anyway, a good start would be to check your system logs in order to see what happened during the boot process and after it. I am sure you will find something. If you have access to your menu, go to **System -> Administration -> System Log**, or better if you want to have access to all of your system logs, open a terminal, go to the */var/log* folder and read the log files from there with e.g. nano.

The OS maybe went PUFF as you say but it logs everything, so even if it didn't give you something to see on the screen, all the info it's there for you to analyse; check your logs...

---

### Post by Chymera on 2007-07-29
=)))) good idea, but wait! theres so much info in there that the little scrollbar has been rendered to its minimum size, oh and wait, ill probably have to look up each line to understand what it says, because, quite frankly, 
> 
Jul 29 01:12:20 chymera-desktop kernel: [   18.342303]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
dosnt tell me anything. But wait! theres more: just as the ubuntu felt like crashing yesterday; this morning, after about 15 reboots and one of the checks it runs every 26 reboots, it felt like mounting my ntfs partitions again. 
Yet the ubuntu thought i may not deserve a full comeback just yet... So it messed up my, actually its, splashscreen, so that it freezes up halfway through making the first 2 icons that should appear on it opaque. And of course, the last part which is loaded (of any window i choose to open at startup) is the titlebar (along with the border). Oh and it thought i might be getting too fond of my semitransparent panels, so, seeing as it believes i  am not worthy of it, it decided to defy me once more. 

[[IMG]http://img182.imageshack.us/img182/8766/screenshot9xp9.th.png[/IMG]](http://img182.imageshack.us/my.php?image=screenshot9xp9.png)

how do you keep your ubuntu happy and peaceful?

---

### Post by deadgobby on 2007-07-29
As I told you before. Not being nice = no help!!! So I am not going to tell you how to fix your problem.

---

### Post by Chymera on 2007-07-29
If you expected to get ars*-kissed for telling me to install smth i obviously already had... tough luck. And if you dont know the answer to my problem, at least dont spam.

---

### Post by xl_cheese on 2007-07-29
I've been frustrated with Ubuntu also.  I've had various issues with it as well.  Had to reinstall 4 times during the 3 months I've been using it.

From the looks of your panels maybe your theme has something to do with your boot problems?  Try changing it to a default one.  I dunno.

---

### Post by Chymera on 2007-07-29
thanks for the advice, but, that is no theme. I have just selected a pic made by myself as the background for the panels, and anotherone as the desktop background. The rest is the standard metacity ubuntu theme.

any other ideas :confused:

---

### Post by deadgobby on 2007-07-29
Yes, I do! Please start being nice and start from the basics. All so say say please and thank you. 
[http://ubuntuclips.org/](http://ubuntuclips.org/)
[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
[http://www.unix-tutorials.com/tutorials.php?os=Ubuntu](http://www.unix-tutorials.com/tutorials.php?os=Ubuntu)
[http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by Chymera on 2007-07-30
PLEASE stop spamming in my threads, THANK YOU.
oh and 10x for the links, theire nice, but i doubt they have anything to do with my problem...

---

### Post by deadgobby on 2007-07-30
They are not spam and yes I read your other threads/post and you are the same way. I posted links to answer your question. It can be found with some reading.

---

### Post by kostkon on 2007-07-30
You said you did not find any useful message in your logs, OK. Maybe, somehow, your current Gnome session got destroyed, some files were corrupted or something like that.

Did you try to log in as a different user? Why not try to make a new user, log in and see if you have the same problems.

If you see that indeed your session is not working well (i.e. the new user's desktop is OK), then search the forum here for ways to fix it.

I hope I helped you somehow...

---

### Post by Chymera on 2007-07-30
It actually kind of sorted itself out, the bugs began to disappear one by one. Im still left with that transparency issue though, and tomboy starts at startup even though ive deactivated it from the sys>pref>sessions, not only as tray but as a search window. Im hoping ill get rid of these problems once i upgrade to gibbon.... I cant help feeling that despite its good apparence ubuntu has been puzzled together in a kind-of make-shift manner.

---

### Post by stchman on 2007-07-30
> **Chymera said:**
> ok, ive just about had it with ubuntu; i can live with the fact that 5.1 doesnt work, i can live with the fact that ive wasted about 15 dvds because gnomebaker graveman and xfburn suck, i can live with the fact that it takes about 2 weeks to set up everything you want, i can live with the fact that WinE sucks and cant get 4-year old games to work (even though on the official website it says they work), and so on...

BUT CAN ANYBODY TELL ME WHY THE HELL, after i rebooted in windows so i could get some stuff done in cs3, THE UBUNTU HAS JAMMED! it takes about 2 minutes to load the desktop (ie. i get a very basic desktop after logon and then after 2 minutes all the stuff that should run on startup appears), and it dosnt mount my 2 ntfs partitions. WTF? you ppl call windows unreliable? SEEING AS WITHOUT EVEN ONE ERROR MESSAGE TO TELL ME WHAT HAPPEND THIS OS GOES "PUFF"?

I have an Audigy 2 and the 5.1 works fine.

Try K3B, it is the best burner for Ubuntu.

If you want to play Windows XP games then keep XP around and dual boot.  That is what I do.

---

### Post by Chymera on 2007-07-30
I have a CMI8738 card, with philips speakers and it DOSNT work, ill try the burner out,  i do have win xp in dual boot, but do you have any idea as to how i could solve my MAIN problem now?

---

### Post by LaRoza on 2007-07-30
> **Chymera said:**
> ok, ive just about had it with ubuntu; i can live with the fact that 5.1 doesnt work, i can live with the fact that ive wasted about 15 dvds because gnomebaker graveman and xfburn suck, i can live with the fact that it takes about 2 weeks to set up everything you want, i can live with the fact that WinE sucks and cant get 4-year old games to work (even though on the official website it says they work), and so on...

BUT CAN ANYBODY TELL ME WHY THE HELL, after i rebooted in windows so i could get some stuff done in cs3, THE UBUNTU HAS JAMMED! it takes about 2 minutes to load the desktop (ie. i get a very basic desktop after logon and then after 2 minutes all the stuff that should run on startup appears), and it dosnt mount my 2 ntfs partitions. WTF? you ppl call windows unreliable? SEEING AS WITHOUT EVEN ONE ERROR MESSAGE TO TELL ME WHAT HAPPEND THIS OS GOES "PUFF"?

If you want help, could you please state the problem, what happened before the problem occured, and when everything was working fine. 

Your first paragraph hides the issue, and is unneccessary. Remember, people usually remember the first and last thing they read, the "primacy" and "recency" effect, so word your posts accordingly.

Your second paragraph manages to blame a computer and software for a possible human error, and insults the people who can probably help you.

If you want to use Windows, you are free to do so, remember.

---

### Post by Chymera on 2007-07-30
did i say that i want to use windows? i dont, thats why im trying ubuntu out!!!

To tell you what happened before it "broke"? Thats the reason why im so appaled by what just happened, NOTHING happened before the problem occured... i was just restarting the computer and voila: jammed ubuntu.
But im over that now, as you may have noticed if you read at least my 2nd post. The ubuntu kindly repaired itself just as unexplainably as it broke, leaving only some minor, but still very annoying bugz behind.

---

### Post by pak33m on 2007-07-30
Chymera,

> Im hoping ill get rid of these problems once i upgrade to gibbon....

Followed your thread and wanted to warn that upgrading to Gutsy Gibbon could potentially break your system as it is still in development, thus causing you more problems.  This warning does not just come from me but Ubuntu developers as well.

Hope this helps!

---

### Post by LaRoza on 2007-07-30
> **Chymera said:**
> did i say that i want to use windows? 
No, but you sound like you think the world will end if Ubuntu doesn't work.
> **Chymera said:**
> 
To tell you what happened before it "broke"? Thats the reason why im so appaled by what just happened, NOTHING happened before the problem occured... i was just restarting the computer and voila: jammed ubuntu.

NOTHING always happens... I am most curious as to what this NOTHING is that causes computers to break "FOR NO REASON". This is a classic user problem script, I've heard it many times.
> **Chymera said:**
> 
But im over that now, as you may have noticed if you read at least my 2nd post. The ubuntu kindly repaired itself just as unexplainably as it broke, leaving only some minor, but still very annoying bugz behind.
The OS is more powerful than the human...

---

### Post by misfitpierce on 2007-07-30
Also on the fact of old games you may need to install graphics drivers for whatever card you may have.

---

### Post by Chymera on 2007-07-30
> **pak33m said:**
> Chymera,



Followed your thread and wanted to warn that upgrading to Gutsy Gibbon could potentially break your system as it is still in development, thus causing you more problems.  This warning does not just come from me but Ubuntu developers as well.

Hope this helps!

Ill only upgrade when its good to go, my system is already pretty shaken

---

### Post by Chymera on 2007-07-30
> **LaRoza said:**
> No, but you sound like you think the world will end if Ubuntu doesn't work.
And that to you equals the fact that i want to use windows?

> **LaRoza said:**
> NOTHING always happens... I am most curious as to what this NOTHING is that causes computers to break "FOR NO REASON". This is a classic user problem script, I've heard it many times.
You sound like the help-line operators from microsoft, of course its the users fault, because the os is PERFECT and bill gates along with the ppl at redmond (in your case probably linus torwalds and the ppl working on ubuntu) are god. At least the operators only say so because they're paid to do it, in your case its worse, you really believe it.

---

### Post by LaRoza on 2007-07-31
> **Chymera said:**
> And that to you equals the fact that i want to use windows?


You sound like the help-line operators from microsoft, of course its the users fault, because the os is PERFECT and bill gates along with the ppl at redmond (in your case probably linus torwalds and the ppl working on ubuntu) are god. At least the operators only say so because they're paid to do it, in your case its worse, you really believe it.

0. No, but you seem to believe we are here to serve you absolutely, we are just users remember, helping each other. You wouldn't use that attitude, I hope, face to face, so why do it here?

1. You told us something went wrong, with nothing else to go on. Then you expected us to help. This happens all the time with any OS. If your car, if you have one, broke, you would tell the mechanic MUCH more, even if you don't really understand cars. You assume we know everything about the situation. I don't believe any OS is perfect, but if something goes wrong, I am attentive to the situation, so I can get help.

---

### Post by Chymera on 2007-07-31
I dont believe anyone should **serve me absolutley**, and you making such a statement speaks of the fact that you dont really want to help, but rather to argue, because, in your very personal opinion (which i cant say i really care about), my conduct is not appropriate for the likes of you.
Why wouldnt i use this attitude face to face? Would your personal appearence by any means keep me from telling you off? i doubt it.

If you think answering my first post is undeserving of your time, then by any means, *dont answer it*! If i post something, then i probably went through it before stating it, if you choose not to believe me then *just dont*! but at least dont try to convince me that you have better knowledge of what i did beforehand. 

And dont go spoiling my threads will you? perhaps some less arrogant people, who can understand that in such a situation you cannot leave out any form of aggression from your initial post, and who take the information i give for granted would have answered; if it weren't for ppl like you who try to turn a software related thread into an argument. I see it finally dawned on you to pm me about it. It would have been smart of you to do so from the beginning, seeing as you felt no need to give any advice related to this threads topic.

---

### Post by Siph0n on 2007-07-31
hehe ubuntu ftw :)

---

### Post by r4ik on 2007-07-31
> **Chymera said:**
> I dont believe anyone should **serve me absolutley**, and you making such a statement speaks of the fact that you dont really want to help, but rather to argue, because, in your very personal opinion (which i cant say i really care about), my conduct is not appropriate for the likes of you.
Why wouldnt i use this attitude face to face? Would your personal appearence by any means keep me from telling you off? i doubt it.

If you think answering my first post is undeserving of your time, then by any means, *dont answer it*! If i post something, then i probably went through it before stating it, if you choose not to believe me then *just dont*! but at least dont try to convince me that you have better knowledge of what i did beforehand. 

And dont go spoiling my threads will you? perhaps some less arrogant people, who can understand that in such a situation you cannot leave out any form of aggression from your initial post, and who take the information i give for granted would have answered; if it weren't for ppl like you who try to turn a software related thread into an argument. I see it finally dawned on you to pm me about it. It would have been smart of you to do so from the beginning, seeing as you felt no need to give any advice related to this threads topic.

Keep the attitude sweety  :)
It will get you somewhere for sure.:popcorn:

---

