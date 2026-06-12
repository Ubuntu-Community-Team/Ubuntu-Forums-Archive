---
title: "Text/Programming editor with some features"
date: 2013-01-06
forum: General Help
---

### Post by Jaoyur on 2013-01-06
I'm looking for a text editor to write programms in C,java,html,C++,UNIX scripts etc.
  I have used **Gedit**, **Geany**, **Eclipse**, **Code::Blocks** and **Kate** but each one has something that I found wrong.
  I need following features:
  
[LIST]
[*]it would be great if it could integrate with a compiler (gcc...) like geany
[*]it should allow changing/downloading themes both for the application and syntax highlighting
[*]I would like to print my works with a text editor that supports  black background for printing, I mean it should have the possibility to  invert colors (like code:blocks) in order to print with white background  (inverted colors) or something similar.
[/LIST]
  I have just excluded **Code::Blocks** despite it has good color themes, because when I have printed a file some characters were overlying others.
  I have also excluded **Geany** because it has what I  think is a bug, it's almost about the same problem as with Code::Blocks,  because while using a dark theme (white-on-black background) the file  gets printed with some characters being on white and some on black  background.


  What do you advice? Thanks

---

### Post by roten on 2013-01-06
Try **emacs** it's old but very powerful

---

### Post by Jaoyur on 2013-01-06
> **roten said:**
> Try **emacs** it's old but very powerful

ok thanks i'm downloading it, I found this ppa [https://launchpad.net/ubuntu/+source/emacs23](https://launchpad.net/ubuntu/+source/emacs23), is it the app you said? It seems under updating.

---

### Post by TheFu on 2013-01-06
There is only 1 real UNIX editor, vi, though vim can work in a pinch if you need colors. 

If you are serious about programming on UNIX/Linux, then you should learn the power of vi.  Watch a youtube video of an expert using vi and you will be a convert forever.

On Linux, doing C/C++ development is usually performed using 3 windows.
* editor
* make/gmake  - up arrow <enter> How hard is that?
* debugger - for C++, I use ddd with gdb.
* setup your focus to follow the mouse, but not raise any windows.
It is amazingly efficient after you've ***learned the power of the Linux-side.*** [spoken in my best Darth Vader voice]

***Give in, Luke.***  ***Join me. Together we will rule the universe.***

If you are that picky about your editor AND you work in those languages, why not just patch any of them with source to your liking? Help out others by providing a patch back to the upstream with your fixes.

There is always WINE too, if there is a Windows editor that you like. Notepad++ works under WINE, I hear.

I should also mention that I'm a reformed **emacs** user.  After many months of constantly using **vi-mode** while in emacs, I decided it was time to switch. I fought it for about 3 yrs. Everyone around said to just bite it and an switch all that time. I wish I'd listened 2.5 yrs sooner.

---

### Post by Jaoyur on 2013-01-06
thanks, for now I just need a not so much complicated editor (like emacs :)) to write my C programms.
I use code::Blocks on windows 7 and I wanted to use the same here in ubuntu but I found some bugs I reported on the forum but I had no answers.
What I like in code::Blocks is the possibility to change any color of the C formatted text using settings interface (without terminal or commands like in emacs) so I'd be able to personalize the color scheme and print the file to study it. I tried also gvim that is good in printing file with black background but it's complicated to change settings.

---

### Post by Calinou on 2013-01-06
> **TheFu said:**
> There is only 1 real UNIX editor, vi, though vim can work in a pinch if you need colors.

Geant ftw (use a light theme then!); editor war started. Vim and emacs both suck, we're in 2013, guys.

---

### Post by na5h on 2013-01-06
Why use just one? I use multiple IDE:s myself. 

[Aptana]("http://www.aptana.com/") is great for web developing (has got some nice, dark themes...it's also available as a plugin for Eclipse). [Netbeans]("http://netbeans.org/") is a good all-around IDE and [Eclipse]("http://www.eclipse.org/") the easiest choice if you're into developing Android apps.

Always use the best tool for the job at hand...

---

### Post by Jaoyur on 2013-01-06
thanks, infact I have to use codeblocks or eclipse just to build my file, but I will edit it with something else. In windows 7 I was used to use codeblocks for everything, I don't understand why it has those problems. I prefer codeblocks to netbeans and eclipse because it doesn't not make a project any case, I mean if I just want to make a file .c and then compile it and run I can without creating a project for that

---

### Post by dragonfly41 on 2013-01-06
Try Komodo Edit 7 (the free editor .. not the IDE which is not free)

[http://www.activestate.com/komodo-edit](http://www.activestate.com/komodo-edit)

I've also used Aptana Studio and Jedit.

---

### Post by Jaoyur on 2013-01-07
ok I'm trying Komodo and Aptana.

However, while using different programs I made my conclusions. I like something like codeblocks I mean a not "project-oriented" IDE (so no eclipse, kdevelop, netbeans etc...), something with the possibility to use gcc inside the program (like geany or codeblocks) and with color personalization like codeblocks or kate. 
So codeblocks would be the best for me, but it has printing problems, infact I have opened this --> [http://forums.codeblocks.org/index.php/topic,17340.new.html#new](http://forums.codeblocks.org/index.php/topic,17340.new.html#new)
So the second best for color personalization and printing is Kate, but it just has the terminal inside and I have to write the commands to use gcc. So I'll keep you updated:) 
thanks

---

### Post by TheFu on 2013-01-07
> **Jaoyur said:**
> ok I'm trying Komodo and Aptana.

However, while using different programs I made my conclusions. I like something like codeblocks I mean a not "project-oriented" IDE (so no eclipse, kdevelop, netbeans etc...), something with the possibility to use gcc inside the program (like geany or codeblocks) and with color personalization like codeblocks or kate. 
So codeblocks would be the best for me, but it has printing problems, infact I have opened this --> [http://forums.codeblocks.org/index.php/topic,17340.new.html#new](http://forums.codeblocks.org/index.php/topic,17340.new.html#new)
So the second best for color personalization and printing is Kate, but it just has the terminal inside and I have to write the commands to use gcc. So I'll keep you updated:) 
thanks

You are fighting the Linux way.  You will not be happy if you keep doing that.  Might I suggest you find a Linux programmer to mentor you?  Seems to me you are doing things the hard way.
* vi or vim - I really do not care how you edit code. None of my business, but I've never been on any embedded router with an editor besides vi.
* **gmake** to tell gcc what to do. Makefiles are extremely powerful or trivial. Nobody should call gcc directly.  A 10 line Makefile is good enough to start. Later you can add automatic dependency building and other fancy things.  I agree that project based IDEs are crazy, but when Microsoft abandoned make in the mid-1990s, my team switched to using gmake 100% on all platforms.
* use** indent** or something similar to enforce code standards, curly bracket locations, and spacing.
* use a code beautifier to create pretty, colored, HTML for printing, if you must.

Why is leaving the editor such a big deal to build code? It is just a mouse slide, up-arrow<enter> key. Hardly a big deal.

I must admit that I've used geany more than a few times. It isn't too bad, but has crashed on me.  Vi has never crashed. Not once.

---

### Post by Impavidus on 2013-01-08
> **TheFu said:**
> 
Why is leaving the editor such a big deal to build code? It is just a mouse slide, up-arrow<enter> key. Hardly a big deal.
If you like, in vim you can use the [FONT=Courier New]:make[/FONT] command inside the editor to run make and compile. You could consider using vim (like I do), the manual (vimbook) only has 572 pages.

Or you could use something simpler and use the mouse slide (or ctrl+alt+left arrow) - up arrow - enter method.

---

### Post by 1clue on 2013-08-07
I use sublime text 2.  It's not free, and it's not in the repository.  It is, however, very good and works on Mac, Windows and Linux.  One license per user, any number of machines.  Configuration is by editing files, which I think is awesome, and there are a whole lot of plugins.  The app itself is tiny, and the plugin idea lets you tailor it to your needs rather than starting with something huge with features you never use and have to learn to ignore.

The default background is a sort of dark chocolate, and it isn't printed that way.

Note that this is an EDITOR and not an IDE.  It handles syntax highlighting, has excellent search features but if you have multiple functions with the same name it doesn't know which one you mean.

The editor I used almost exclusively for the first 15 years of my career or so is vi and then vim.  It took a long time before I found any editor or IDE that was better than that, including payware.  Eclipse/STS is the first IDE I had to admit was better, and that's because of the IDE functionality.

Vim is available on pretty much any UN*X.  Commercial versions they might not have it, but they probably have vi.


> **TheFu said:**
> There is only 1 real UNIX editor, vi, though vim can work in a pinch if you need colors. 

If you are serious about programming on UNIX/Linux, then you should learn the power of vi.  Watch a youtube video of an expert using vi and you will be a convert forever.


Dude.  If you think that color is the only way that vim is better than vi, you know a tiny fraction of the commands.  :set nocompatible, and start learning.

---

### Post by btindie on 2013-08-07
Take a look at **bluefish**&#8203;.

---

### Post by gleedadswell on 2013-08-07
First of all, the earlier advice na5h about using multiple editors/IDEs to suit the project is probably the best all-around advice.

That being said, given the preferences you've stated, I'm going to second the earlier advice about emacs.  If you like an editor that does not generate projects and which can run gcc from inside the program it is probably what you want.  I don't think it is easy to modify color schemes on the fly (but I've never tried), but there are lots of color themes available.  I don't know how well it works for printing as I never print anything if I don't absolutely have to.

I find running the compiler from within emacs particularly nice because (like a more modern IDE) when it generates error messages you can click on them and be brought directly to the line of code that generated the compile error.  This is obviously a lot nicer than always running the compiler from the command line in a separate window.  But, there are still times when it may be preferable to go to the command line for compiling (e.g. when you want to generate a single .o file within a larger project).

---

### Post by gleedadswell on 2013-08-07
... and since this discussion is sounding a lot like it, you should really read this piece of humour about text editors:

[http://www.gnu.org/fun/jokes/ed-msg.html](http://www.gnu.org/fun/jokes/ed-msg.html)

---

### Post by 1clue on 2013-08-07
That's hysterically funny.

---

### Post by zealibib slaughter on 2013-08-07
ok I have to do it, ed is the standard linux editor.

but seriously +1 for bluefish

---

### Post by 1clue on 2013-08-07
> **gleedadswell said:**
> ... and since this discussion is sounding a lot like it, you should really read this piece of humour about text editors:

[http://www.gnu.org/fun/jokes/ed-msg.html](http://www.gnu.org/fun/jokes/ed-msg.html)

This is STILL funny.

You had to have been there I guess.

I was.

---

