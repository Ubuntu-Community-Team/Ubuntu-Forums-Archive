---
title: "Ubuntu is hungry!"
date: 2007-11-12
forum: General Help
---

### Post by Chymera on 2007-11-12
I am aware that Ubuntu isn't a lightweight distro and that consequently, even when compared to vista, the performance-to-memory ratio isn't a whole lot better..... And all in all it's pretty logical.

However, recently i have been experiencing something which i strongly hope is a bug of some sorts....

I have 3 running applications 
Pidgin ( 1 window, 1 tab)
Exaile (playing an .mp3 file)
Gimp (the usual 3 windows, with an a4 document, with 10 layers out of which 7 are active, and cover about one forth of the page)  

[[IMG]http://img106.imageshack.us/img106/6994/screenshotwr0.png[/IMG]](http://imageshack.us)


Now, allthough the system monitor can't say very much about it, I believe Gimp is the prog that is eating up all that memory.... if someone would be kind enough to tell me what excuse a flintstone app like the gimp has for eating up 8 times the memory ps cs 3 does... i would be grateful...

---

### Post by mcduck on 2007-11-12
Try running 'free -m' in a terminal, and then look at the '-/+ buffers/cache'-line. This is where you see how much memory you are really using.

Linux uses all your available RAM, what's not used by running programs is used as a disk cache to store data you have recently accessed. When some program needs more memory data from cache is dropped. Anyway, if the memory is not used it's wasted ;)

---

### Post by aysiu on 2007-11-12
Can we assume you've read this?
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by Chymera on 2007-11-12
No, you cannot assume that.... but considering the degree to which my machine was slowed down, I believe the system monitor actually showed less memory being used than was actually the case. I couldn't even move my cursor to launch the system monitor, luckily i had it set to Ctrl+Alt+Del.... Not to mention the computer locked up after taking that screenshot.

I did rum free -m (now, 1x firefox, 2x pidgin, 1x nautilus, 1x exaile, 1x openoffice, and compiz+ screenlets of course), and surprizingly, instead of using the apparent 912 ram my machine uses only 750... what a relief :-/

---

### Post by gmaniac on 2007-11-12
Although instead of showing us the resources tab you could have shown us the processes tab it must certainly be gimp. But have you realized by selecting an A4 document you created a file that is 2480x3508 pixels!!. Every layer for me shows an addition of 78MB (a hint shown at the bottom of the image). I don't know how photoshop reacts to this, maybe better, but this is gimp. 

PS If you are not in dtp then you most certainly don't have to use that resolution to print something in an A4 paper.

---

### Post by Chymera on 2007-11-12
> **gmaniac said:**
> Although instead of showing us the resources tab you could have shown us the processes tab it must certainly be gimp. But have you realized by selecting an A4 document you created a file that is 2480x3508 pixels!!. Every layer for me shows an addition of 78MB (a hint shown at the bottom of the image). I don't know how photoshop reacts to this, maybe better, but this is gimp. 

PS If you are not in dtp then you most certainly don't have to use that resolution to print something in an A4 paper.

Well I would have also taken a screenshot of the processes tab if the computer hadn't locked up.... however I doubt that would have helped, since in linux as well as in windows, the memory usage on the process tab never adds up to the actual resource usage....

I have realized what 300 dpi means since last millenium, thank you. But did you realize that working with the exact same dpi on ps cs1, 2 years ago, on a machine had 1/4 the processing power of my current one and 1/2 the ram I had virtually NO hardships? And mind you, gimp is more like paint than like ps cs1 by means of "things it can do".... So i really cant imagine how it coud possibly fill all that memory...

---

### Post by yellowbread on 2007-11-12
> Try running 'free -m' in a terminal, and then look at the '-/+ buffers/cache'-line. This is where you see how much memory you are really using.

This always gives the same result as the system monitor for me. And if you look at how much swap space is being used, and the description of the symptoms, it is clear that a lot of memory is actually being used.

To the OP, i probably can't offer any useful suggestions, but a few questions: what version of Ubuntu are you running? Why do you think gimp is the culprit?

---

### Post by Chymera on 2007-11-12
I am running 7.10, and i believe gimp to be the culprit because, even though it's preposterous for gimp to use more than lets say 300 mb of ram, it would be a whole lot more incredible for exaile or pidgin to do this....

---

### Post by mcduck on 2007-11-12
How about Compiz then? Do you have nVidia graphics card? There's a confirmed memory leak with Compiz&nVidia-combination..

I find it kind of hard to believe that Gimp would be the problem, as I use it all the time for pretty high resolution images with tens of layers, with no problems.. (Btw, comparing Gimp to Paint is blasphemy. It can do all the stuff you can do with Photoshop, there just isn't all the nice&easy tools for some things so you need to know how to do them yourself instead ;))

---

### Post by yellowbread on 2007-11-12
32 or 64 bit?

As gmaniac suggested, look in the processes tab at gimp. How much memory does it report being used?

---

### Post by Chymera on 2007-11-12
> **yellowbread said:**
> 32 or 64 bit?

As gmaniac suggested, look in the processes tab at gimp. How much memory does it report being used?

64 bit, read the thread before posting, thank you

---

### Post by Chymera on 2007-11-12
> **mcduck said:**
> How about Compiz then? Do you have nVidia graphics card? There's a confirmed memory leak with Compiz&nVidia-combination..

I find it kind of hard to believe that Gimp would be the problem, as I use it all the time for pretty high resolution images with tens of layers, with no problems.. (Btw, comparing Gimp to Paint is blasphemy. It can do all the stuff you can do with Photoshop, there just isn't all the nice&easy tools for some things so you need to know how to do them yourself instead ;))

:)) do all the stuff you can do with ps :)) hmmm... can you do 32bit color? 24 at least? some CMYK layering perhaps? ok, than maybe some layer effects? layer grouping? multiple layer select? than surely you can ad at least  some saturation/hue/sharpness/etc mask layers... NO, you can't.... I had similar discussions with a lot of gimp fanboys and would gladly link you to one of them (since I don't want this spoiling the thread), if I had the time to look them up...

Now, as for my actual problem.... you're asking me if I have nVidia.... well I probably have either nVidia or ati, are you by any chance trying to say that Compiz has HUGE issues with both major gfx cards producers? Why is anyone still using it?

I get this problem when working with the gimp, i also got smth simillar (just not as severe) with inkscape.... thats why i didn't think of blaming it on compiz...

---

### Post by mcduck on 2007-11-12
> **Chymera said:**
> :)) do all the stuff you can do with ps :)) hmmm... can you do 32bit color? 24 at least?ok, than maybe some layer effects? layer grouping? multiple layer select? than surely you can ad some saturation/hue/sharpness/etc mask layers... NO, you cant.... I had this discussion with a lot of gimp fanboys and would gladly link you to one of them since I dont't want this spoiling the thread, if I had the time to look them up...

Now, as for my actual problem.... you're asking me if I have nVidia.... well I probably have either nVidia or ati, are you by any chance trying to say that Compiz has HUGE issues with both major gfx cards producers? Why is anyone still using it?

I get this problem when working with the gimp, i also got smth simillar (just not as severe) with inkscape.... thats why i didn't think on blaming it on compiz...

I said that I can get all the same results, not that Gimp would have all the same tools. ;) I'm not a fanboy of any program, I use both Photoshop and Gimp, Illustrator and Inkscape, and this far I've been able to easily do every single thing I need with both Adobe's and free programs. If you mean 32 bits per single channel, then you should look at Cinepaint (which is a version of Gimp, made to do tasks that Photoshop isn't able to handle like _extremely_ high resolutions, many image formats, and also 32-bit color channels which Photoshop gained only very recently..)

And I didn't say that Compiz would have any huge issues with all major graphics card manufacturers. I said that the current version has a confirmed memory leak that causes problems for some people who have nVidia's graphic card. People are still using it because it works without any problems for most of us. But since you are having problems, it might be a good idea to check that one.

Anyway, if something is eating your RAM, it would be a wise thing to check what's eating it instead of just guessing..

---

### Post by Chymera on 2007-11-12
> **mcduck said:**
> I said that I can get all the same results, not that Gimp would have all the same tools. ;) 

And I didn't say that Compiz would have any huge issues with all major graphics card manufacturers. I said that the current version has a confirmed memory leak that causes problems for some people who have nVidia's graphic card. People are still using it because it works without any problems for most of us. But since you are having problems, it might be a good idea to check that one.

Anyway, if something is eating your RAM, it would be a wise thing to check what's eating it instead of just guessing..


How do i check it? 

btw, 32bit color is not a tool... and memory leaks are a major issue


EDIT: editing your post just to get the upper hand in the argument just proves that you have no verticality... so much for the dignity i've mentioned in one of my next posts....

---

### Post by yellowbread on 2007-11-12
> **Chymera said:**
> 64 bit, read the thread before posting, thank you ???

I'm sorry but I don't find anywhere in the thread where it says you are running 64 bit. The reason I'm asking is because I'm trying to figure out if the Compiz/Nvidia bug on 64 bit Gutsy is causing your problem. Since you don't know if you have an Nvidia card, try this: run free-m, open a window, maximize it, close it and run free -m again. Do you see a significant difference?

---

### Post by gmaniac on 2007-11-12
Because it seems you are such an enjoyable person to the ones trying to answer your question here is my question to you.
Why my computer runs slower than the one nasa has to simulate climatic changes ?

BTW i didn't say to you anything about dpi I said **dtp**(Desktop publishing) so read my answer one more time. thank you.

Alternative to photoshop? how about Pixel32 but not free.

---

### Post by mcduck on 2007-11-12
> **Chymera said:**
> How do i check it? 

btw, 32bit color is not a tool... and memory leaks are a major issue

I still didn't say it's a tool. It's not very nice to put words to other people's mouths. Even less when those peoples are using their free time to try to help you.

Memory leak is a major issue for those who suffer from it. That doesn't make it a major issue with all major graphics cards or major issue for everyone.

---

### Post by Chymera on 2007-11-12
> **yellowbread said:**
> ???

I'm sorry but I don't find anywhere in the thread where it says you are running 64 bit. The reason I'm asking is because I'm trying to figure out if the Compiz/Nvidia bug on 64 bit Gutsy is causing your problem. Since you don't know if you have an Nvidia card, try this: run free-m, open a window, maximize it, close it and run free -m again. Do you see a significant difference?

I told you to read the thread because you seem to be missing things: the first one was your question with the process tab: look it up.
Now, you just missed something else, at the top of this page I implied using an nVidia card, something mcduc seems to have understood....

---

### Post by Chymera on 2007-11-12
> **gmaniac said:**
> Because it seems you are such an enjoyable person to the ones trying to answer your question here is my question to you.
Why my computer runs slower than the one nasa has to simulate climatic changes ?

BTW i didn't say to you anything about dpi I said **dtp**(Desktop publishing) so read my answer one more time. thank you.

Alternative to photoshop? how about Pixel32 but not free.

Because your computer is a wreck compared to the one the folks at nasa use.Didn't think of that did you? 
Aside from your aggressive remark; You asked me if I realize how many pixels an a4 document had, that is because of a high dpi.... Its really terrible when people 1) don't try to understand much 2) start geting aggressive because of that 3) jump to conclusions that someone can't understand what they believe to be "insider lingo" ... try to avoid both the first and the second, thank you.

If i wouldn't mind something not being free I'd be using Photoshop right now....

---

### Post by Chymera on 2007-11-12
> **mcduck said:**
> I still didn't say it's a tool. It's not very nice to put words to other people's mouths. Even less when those peoples are using their free time to try to help you.

Memory leak is a major issue for those who suffer from it. That doesn't make it a major issue with all major graphics cards or major issue for everyone.

Here we go again.... well, read the first line of your last post before this one.... you didn't imply that all i've listed were tools? poor english then.... (and please don't go about modifying your post just to get the better bargain off the argument... it's really beneath what i hope to be our dignity...)

Is it me or is everyone more interested in proving they are right than in actually making some constructive remark?

---

### Post by yellowbread on 2007-11-12
Perhaps you could be a little less antagonistic towards the people trying to help you.

If you have this bug that a few of us suspect, it will show up in compiz.real. find the process number ####  for compiz.real, run top -p ####, and watch the number rise rapidly as you do graphics intensive stuff.

---

### Post by Chymera on 2007-11-12
> **yellowbread said:**
> Perhaps you could be a little less antagonistic towards the people trying to help you.

If you have this bug that a few of us suspect, it will show up in compiz.real. find the process number ####  for compiz.real, run top -p ####, and watch the number rise rapidly as you do graphics intensive stuff.

well people seem to "help" me in a quite interesting way, as you may already have noticed....
Now, I didn't exactly understand your instructions, what should i look for? where?

---

### Post by mcduck on 2007-11-12
> **Chymera said:**
> Here we go again.... well, read the first line of your last post before this one.... you didn't imply that all i've listed were tools? poor english then.... (and please don't go about modifying your post just to get the better bargain off the argument... it's really beneath what i hope to be our dignity...)

Is it me or is anyone more interested in proving they are right than in actually making some constructive remark?

We can't fix your problem for you, we can only help you to fix it. And for that you need to actually provide the information we are asking for. So please check which process is actually eating your memory.

Then again, where exactly did I say 32-bit colors were tools? Anyway, if my English skills are more interesting than providing the information needed to solve _your_ problem, there probably is other people in these forums needing help more than you do.. (Did you know that everybody in these forums isn't a native English speaker?)

---

### Post by yellowbread on 2007-11-12
First, find the process number for compiz.real. In a terminal:  ps -e
Find compiz.real in the list and note the process id (1st column).
In a terminal: top -p ####  where #### is the process id for compiz.real.
Leave this running as you do other stuff, like working in gimp, opening a window, maximizing it, closing i,t or one thing that got my memory useage to jump by 15 mB at a time, preview your screen saver. Keep an eye on your terminal running top as you do this stuff.

---

### Post by Chymera on 2007-11-12
@ mcduck:
1) when did I ask you to solve the problem for me? (it's not nice to put words in other people's mouths, etc....)
2) Until yellowbread appeared noone actually told me how to get that info
3) Well, i just told you where you implied that (you dont actually need to say ymth in order to mean it)
4)You don't have to be a native english speaker, neither am i, i also make mistakes, i'm not a grammar nazi, however it's the least you can ask of an interlocutor is to actually understand the meaning of what he himself is saying.

---

### Post by Chymera on 2007-11-12
@ yellowbread
I think i jus did what you said... here's a screen of it [http://img253.imageshack.us/my.php?image=screenshot3ht4.png](http://img253.imageshack.us/my.php?image=screenshot3ht4.png)

---

### Post by yellowbread on 2007-11-12
Yes, that's it. Leave that running and see if it stays at 27mb or continues to rise. If it stays the same, I have no idea what is wrong. If it rises continually its the bug we've been talking about. There are several workarounds, but we'll have to wait for a fixed driver from nvidia to cure it.

---

### Post by gmaniac on 2007-11-12
....Maybe nasa **payed** more than I did and maybe you are creating a file with each layer having a size of 70 MB for gimp to represent. 
Saving the file as xcf with a single layer gives a file with 32 megabyte in size. 
If you **really** wont to work with that size lower the dpi.

What is it that you don't understand? You are using a big image with lots of dpi and gimp (but i wonder how much better photosop handles this at the same dpi)

Although I'm enjoying conversing with people that don't know how to make conversation as much as the next one I must leave. 
cu.

---

### Post by Chymera on 2007-11-12
If you enjoy this conversation, that really tells a lot about your character.... however, at least you seem to have understood what i said this time....  keep it up!

---

### Post by mcduck on 2007-11-13
If it helps you, I tried making the kind of file you had problems with. A4, with 300 DPI resolution, and color photographs on 10 layers, all active, all composited so every layer is visible through each other. 

Both Gimp on my Ubuntu machine and Photoshop CS 3 on my Mac needed about 400MB of memory to keep the file open. Gimp actually a bit less than PS CS 3.

edit. I also should point out that I didn't experience any kind of slow downs or stability issues on either of the setups. When drawing on the 10th layer both programs had noticeable lag, clearly more in Photoshop than in Gimp.

---

### Post by Chymera on 2007-11-13
> **yellowbread said:**
> Yes, that's it. Leave that running and see if it stays at 27mb or continues to rise. If it stays the same, I have no idea what is wrong. If it rises continually its the bug we've been talking about. There are several workarounds, but we'll have to wait for a fixed driver from nvidia to cure it.

I don't think this is it, i left the terminal window open for about 20 hours.... the mem usage did indeed increase but only a bit; now i've just returned home and instead of 27mb its using 70....

---

### Post by Chymera on 2007-11-15
I seem to have found the problem.... when opening the process tab in a very clogged sirtuation I found that the most hungry process was "python" with almost 300 mb 

I killed it, exaile crashed, then i waited some 20 secs, launched exaile again and evrrything seems to be fairly smooth...

Any idea how to stop python from getting hungry again?

---

### Post by mahiyar on 2007-11-15
What an interesting chain of posts, I really learnt a lot here.

---

### Post by mali2297 on 2007-11-15
So Exaile was the hungry thief? They always blame the poor gimp. (Remember Quasimodo?)

A bug was reported just recently:
[https://bugs.launchpad.net/exaile/+bug/162226](https://bugs.launchpad.net/exaile/+bug/162226)

---

### Post by Chymera on 2007-11-15
the hungry process wasn't exaile, but python, tell me if I'm wrong, but i thought they were 2 entierly different things...

---

### Post by bingoUV on 2007-11-15
python is just a programming language. It does not do anything of itself, it just does what it is asked to do. I guess exaile is written in python. Which is why killing python made exaile crash. 

View command line in system monitor, and see the full command of python. You can guess the application name from the full command line.
(edit -> preferences -> processes -> check command line)

edit : python is alleged to be quite a resource hungry language.

---

