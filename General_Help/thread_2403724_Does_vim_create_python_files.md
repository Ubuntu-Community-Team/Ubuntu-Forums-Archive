---
title: "Does vim create python files ?"
date: 2018-10-15
forum: General Help
---

### Post by aubertinsylvain on 2018-10-15
Hi all ! It would be very interesting for me to create python files. I hope it is possible. Thanks

---

### Post by TheFu on 2018-10-15
Any text editor can make python files.
It is up to the programmer to type in the python code.

---

### Post by 1clue on 2018-10-15
Go to your package interface (apt, aptitude, synaptic...) and look for 'python vim' and you'll get python syntax for vim. If it's not there already.

I can't say what's default because vim is my editor, and literally the first thing I do after an install is install vim-nox and syntax files for the languages I use. 

vim-python is the virtual package, and as I see it being provided for vim-nox and 3 other vim variants, you probably already have it on whatever vim you use.

vim-python-jedi is an autocomplete tool for python.

---

### Post by TheFu on 2018-10-15
> autocomplete

What?  Don't programmers know how to code?  We never had autocomplete on tests or at job interviews. Did things change?   ;)

---

### Post by 1clue on 2018-10-15
As a point of fact I hate autocomplete. For some reason it always completes the wrong word for me.

And as for autocomplete on the phone, well let's just say the Internet is full of horrific examples of that.

That said, many of my programmer buddies love the heck out of it. So I thought I'd include it in my results.

---

### Post by aubertinsylvain on 2018-10-15
@1clue I installed vim but was very surprised to find clicking on "Files" on the bar: New Tab, New Window, Close Tab, Close Window. Is that normal ? I expected "save", save as", ect

---

### Post by TheFu on 2018-10-15
vim is a mode-oriented editor.  If you don't know what that means, you'll need to either watch some beginner videos that talk through it or use the vim-tutor (which isn't exactly self-explanatory). There aren't any menus.  gvim has menus, but I don't see the point of using gvim, myself.  If I want menus, I'd use geany or some other lite-editor. Geany is almost an IDE, IMHO.  I think Atom is popular with the Python crowd.

vim in the hands of an expert is an amazing thing.  I love that vim makes moving columns of multi-lines easily.  I used emacs when first beginning on Unix systems, but more and more, I found myself using vi-mode under emacs to get things done. A version of vim is installed on every router and embedded system that I've seen. No other editor is.  So learning at least a minimal amount of vi/vim is necessary for most IT/programmers, but don't feel like you need to force it. Choose whatever editor you like, there are at least 50 others for your consideration.  

NONE of them will enter python code for you. The python programmer is expected to enter that code regardless of the editor chosen.

If I haven't talked you out of learning vim yet, [https://www.youtube.com/watch?v=_NUO4JEtkDw](https://www.youtube.com/watch?v=_NUO4JEtkDw) is a popular vim tutor by someone with only 9 months experience.  IMHO, vim is the most efficient editor that I know, but it takes a little effort to master. Once you know vim, you never have to learn it again.  Sorta like learning a new spoken language.

---

### Post by sp40140 on 2018-10-15
It is very likely that you clicked and got the menu of the "terminal" (gnome-terminal for few who prefer to get technical).
vi (vim) doesn't have on screen menu. 
I get the feeling that you are new to both python and vim. If so, may be you should get just a bit more comfortable with one before you start other one. It can be little tough with both at the same time depending on the time and enthusiasm you dedicate.

---

### Post by 1clue on 2018-10-15
> **aubertinsylvain said:**
> @1clue I installed vim but was very surprised to find clicking on "Files" on the bar: New Tab, New Window, Close Tab, Close Window. Is that normal ? I expected "save", save as", ect

You're new. OK brace for it, every vim and emacs enthusiast on the planet has some significant chance of responding to you.

> **TheFu said:**
> vim is a mode-oriented editor.  If you don't know what that means, you'll need to either watch some beginner videos that talk through it or use the vim-tutor (which isn't exactly self-explanatory). There aren't any menus.  gvim has menus, but I don't see the point of using gvim, myself.  If I want menus, I'd use geany or some other lite-editor. Geany is almost an IDE, IMHO.  I think Atom is popular with the Python crowd.

vim in the hands of an expert is an amazing thing.  I love that vim makes moving columns of multi-lines easily.  I used emacs when first beginning on Unix systems, but more and more, I found myself using vi-mode under emacs to get things done. A version of vim is installed on every router and embedded system that I've seen. No other editor is.  So learning at least a minimal amount of vi/vim is necessary for most IT/programmers, but don't feel like you need to force it. Choose whatever editor you like, there are at least 50 others for your consideration.  

NONE of them will enter python code for you. The python programmer is expected to enter that code regardless of the editor chosen.

If I haven't talked you out of learning vim yet, [https://www.youtube.com/watch?v=_NUO4JEtkDw](https://www.youtube.com/watch?v=_NUO4JEtkDw) is a popular vim tutor by someone with only 9 months experience.  IMHO, vim is the most efficient editor that I know, but it takes a little effort to master. Once you know vim, you never have to learn it again.  Sorta like learning a new spoken language.

Good words.

The UNIX world has a bunch of editors. I'm giving you the simplified version. Pardon me for saying some stuff you may already know.

There are two main families of command-line editors in UNIX. Both are available also on Mac OS and Windows. These editors have a FANATICAL following. It's huge. Like Ford vs Chevy in rural America huge. Some of the online flame wars have been epic. I think it's stupid to argue, they're both extremely capable editors. But they're very different in the way they do things, and people tend to pick a favorite.

One family of editors is based on vi, a commercial product found on commercial UNIX. These editors use a modal system to enter commands, and you flip the mode to type in text. Vim is a free/open source product which is insanely better than vi in every way. I'm in the vim family. Just so you know, what I say is biased even though I'm trying to be fair about it.

The other family is emacs and related editors. Emacs uses control key combinations to activate features. This is more in line with typical mainstream apps, because they use control key combinations too.

Both families have a really steep learning curve and you'll hate them long before you ever love them. But keep reading.

Here's the deal:

UNIX is an amazing operating system. Contrary to popular belief, most UNIX systems have no GUI installed. Most UNIX systems don't have a person sitting in front of them. This is even more true today that it has ever been. Virtual machines allow many operating systems to run concurrently on the same hardware, and most of "the cloud" is some sort of UNIX system. Those systems are servers running to provide a service. They have the required software and absolutely nothing else. They get no benefit from GUI apps and so there is no GUI. Even though both vi and emacs were written before GUIs were common on UNIX systems, they are every bit as pertinent today as they have ever been.

You can and probably should learn a GUI editor or IDE. You likely will learn many over the years. But you should also seriously consider what happens when a GUI is not available. If you actually spend a lot of time with Linux/UNIX, you WILL eventually need to do a lot of remote access. Using a GUI by remote sucks. And when the remote system simply has no GUI you're stuck with the command line. You can either suffer through it or you can own it, and by owning it I mean learn about the tools that are available and have been specifically designed and tweaked over decades to make remote command-line access completely painless. Most UNIX administrators who have been at it for any time don't even want a gui on their systems.

I'm not going to push you to one or the other, but I'm going to strongly urge you to do diligent research and pick one. Or both, but usually people settle on one or the other.

Both vim and emacs are extremely powerful programming editors. They both have a huge array of features, programming language support for syntax highlighting and such, the list goes on. They both support plugins. They both easily allow use of regular expressions to search and replace, and they both allow you to send all or part of the file you're editing to an external UNIX command.

UNIX (and Linux) are full of programming tools, like ctags and tmux. Using several tools together, you can essentially create your own IDE and that IDE will not be lacking in comparison to any other IDE you would care to try. Some features of one might be better than the other, but with vim or emacs you can add as many tools as you want.

I know you just installed Vim and have menus, but neither vim nor emacs requires or in my opinion benefits from menus. It requires nor benefits from a mouse. I use vim-nox which means that it's the pure thing, nothing with pointy-clicky junk cluttering up my screen.

Each of these editors, and all of the tools, have a learning curve. The learning curve sucks, but it's worth it. Both vim and emacs are actively developed, they're not antique anything.

What is an IDE?

An IDE is an interactive development environment. People assume there is magic within. It's not true, and in fact most IDEs have so many features -- all with a little button or menu item to activate them -- that you can hardly get anything done for searching through all the places to click. An IDE is expert software. It takes time to learn how to use it, how to become proficient. But the worst part is that most programmers don't use half of the features that their IDE wastes screen real estate showing to you.

At its core, an IDE is an editor with some easy-to-get-at features focused on building and running the app you're using. The less context switching you have the more work gets done.

 I've been a professional computer programmer since the early 90s. I've been a UNIX/Linux programmer since 1996. I've used several flavors of commercial UNIX and many distributions of Linux, several of which no longer exist.

As a professional programmer I've tried out most of the editors that have touched UNIX systems during that time period. Free editors, free IDEs, closed-source editors, closed-source IDEs, and even a couple pay-a-huge-wad-of-cash IDEs. I still use vim for about half of my work. Right at the moment most of the rest is using Sublime Text 3, a commercial product which runs in a GUI, but still simple and elegant and extremely extendable. All that money, all those editors and I'm still using vim on the command line. What I'm saying here is that the investment in time and effort of learning vim or emacs will stay with you for a long time if you actually use it.

You can go to youtube and see tons of videos when you search for 'vim ctags tmux'. It's good to watch one or two of those, but really you should get basic familiarity with the idea and the end goal, and then use tutorials from the organizations supporting each tool individually.

Tools I mentioned:

ctags is a tool that scans your source code to locate features of your code, like classes (source files) and function/procedure/method headers. So you can automatically navigate to the correct point when you want to see a function definition, for example. You use the information generated by ctags in your editor so that you can find the appropriate spot.

tmux is a terminal multiplexer. It allows many shells to be activated within a single terminal session. Think of this as tabs in your editor, or tabs in your command line terminal. It has many really neat features like the ability to open many tabs, many editors and many running commands, then disconnect from the session and come back hours or days later from a completely different computer, connect to your session and see what happened while you're gone. Or, two or three or ten people can login to a user account on the same remote system, and connect to the same tmux session, and everyone sees what the presenter types.

tmux can be thought of as a 'window manager' for a text login. It's extremely flexible, and you can create configuration files or scripts to set up your session. I use it locally on my desktop because it's every bit as useful there. My terminal app has a tab for each computer I'm logged into, and then a tmux session in each tab. Each host I login to has a tmux script configured to open a 'window' for each significant task I use on that specific host, change directories, and optionally to run a command in each pane. My local setup has a tmux session for each code branch of the software I write, so that when a customer calls I have what they need right there, ready to go.

There are many more tools, but your editor+ctags+tmux is a core combination that gets you to a basic development environment. More importantly, using these tools does not clutter up the screen much at all, and as little screen real estate is used in the default, you can edit your settings to make it use even less.


I'm sorry this post sort of spun out of control, but there's not much I think I want to chop out. Sorry for the rant.

---

### Post by aubertinsylvain on 2018-10-16
Hi all ! I configurated vim. It works very well. I ask myself_: is vim the most sure way to create python files_ .. I say that because with geany I had many times problems on indentation(specialy with tabs.)

---

### Post by TheFu on 2018-10-16
Using tabs or not for indentation is an important decision. There are purists who only use tabs.  I'm not in that group.  I only use tabs where the language requires it, like in a Makefile.  Everywhere else, I replace tabs with 4-spaces.

I think something you mean is being lost in translation.  If you want to make python files, **any editor** can do it.  It is up to the programmer to make python code and has little to do with the editor.

---

### Post by 1clue on 2018-10-16
More importantly, when multiple people are coding on the same project you must all agree on indentation practices.

Personally I feel that we should use tabs from beginning of line to the first darkspace, with the single exception of a space before a * on a c-style comment so the *s line up. After that, no tabs at all. However my entire team feels I'm sick and twisted and should not be trusted due to that preference.

The thing is, we all differ on how many spaces an indent should have. And truth be told, we have some files checked in with a variable amount of indent, and the other files are indented per the preference of whoever first committed the file. Which I think is ridiculous. A tab indent allows people to configure their editor so their indents match their preference, and nobody is left looking at indent widths they're uncomfortable with.

You might consider commit rules for your project, to validate code practices before a developer is allowed to commit. It will help even if you are the only committer.

---

### Post by 1clue on 2018-10-16
> **aubertinsylvain said:**
> Hi all ! I configurated vim. It works very well. I ask myself_: is vim the most sure way to create python files_ .. I say that because with geany I had many times problems on indentation(specialy with tabs.)

What exactly do you mean here?

As with any language you must comply with the language specs. That's on you, not on the editor. Your editor may hook into the compiler and offer easy access to errors posted by the compiler, but that's additional hooking up specific to the language you use. Personally I don't like that "feature" of most IDEs so I've never tried to implement it with vim.

---

### Post by TheFu on 2018-10-16
Last time I checked, Python was interpreted, not compiled.  Do people pre-compile it for better performance?

---

### Post by The Cog on 2018-10-16
> **TheFu said:**
> Last time I checked, Python was interpreted, not compiled.  Do people pre-compile it for better performance?

This explains quite well. It's nothing to do with the editor:
[https://stackoverflow.com/questions/8822335/what-do-the-python-file-extensions-pyc-pyd-pyo-stand-for](https://stackoverflow.com/questions/8822335/what-do-the-python-file-extensions-pyc-pyd-pyo-stand-for)

---

### Post by TheFu on 2018-10-16
Seems to be a convenience thing and mostly handled automatically, as needed.
> A program doesn't run any faster when it is read from a &#8216;.pyc&#8217; or &#8216;.pyo&#8217; file than when it is read from a &#8216;.py&#8217; file; the only thing that's faster about &#8216;.pyc&#8217; or &#8216;.pyo&#8217; files is the speed with which they are loaded. - from that stackoverflow link.

---

### Post by 1clue on 2018-10-16
Sorry I'm not a python user. In any case the editor is not responsible for determining if code is executable or not. The compiler or interpreter is. This is a good thing, because if you have an error in your editor's rulebook then it may tell you you're not be able to execute code which your compiler would actually execute correctly, and not detect real errors in your code. It happens all the time that some editor's syntax checker is wrong.

This is, again, a distinction between an IDE vs an editor with a few well-chosen tools. If you use a good editor and get real benefit from a tool, you can easily add it to your process. If you use an IDE have a built-in tool that misbehaves you may spend hours or days trying to figure out what the problem was, and then spend more time trying to figure out how to turn off the misbehaving feature.

This is also the reason I swore off IDEs some time back. I still look at new ones, but I haven't used one for development for years. Too much screen used for buttons and panels I don't use, and then when a tool misbehaves it leads me down the wrong track. I'm much more comfortable with good documentation and the actual compiler/interpreter.

---

### Post by The Cog on 2018-10-16
> **TheFu said:**
> Seems to be a convenience thing and mostly handled automatically, as needed.
I think you miss a point here. The reason .py files don't run any faster than .pyc files is that .py files are automatically compiled as they load, even if the compiled bytecode does nto get saved. Saving the .pyc saves on re-compiling time as a module gets loaded next time round. And yes, it's all automatic and convenient.

Of course, the bytecode is interpreted - there is an argument over the precise definition ov interpreted vs compiled to be had.

---

### Post by sp40140 on 2018-10-16
Is vim the most sure way to create python files?
For me, it is. As I always use vi for coding and editing files.
For you, it might be or might not be.
Use the tool which you are most comfortable with.
I love vi but don't hate on people who use Emacs/ Eclipse / any other IDE or even notepad++.
What you need to understand is vi is just a tool. Use it if you like it and are comfortable with it. If not try something else.

---

### Post by 1clue on 2018-10-16
> **The Cog said:**
> I think you miss a point here. The reason .py files don't run any faster than .pyc files is that .py files are automatically compiled as they load, even if the compiled bytecode does nto get saved. Saving the .pyc saves on re-compiling time as a module gets loaded next time round. And yes, it's all automatic and convenient.

Of course, the bytecode is interpreted - there is an argument over the precise definition ov interpreted vs compiled to be had.

Not sure if I'd say byte code is interpreted. The initial steps of reading the text, lexically analyzing and tokenizing it have been taken care of, and the byte code is more of a list of links to pre-compiled units of work, with data references passed in. That fact absolutely improves speed over a purely interpreted language.

I'd almost say it's compiled for a VM to execute, but that's too far in the other direction. But in one instance I can think of it is exactly that. Java compilers "compile Java source into byte code." But the byte code is literally executed on a virtual machine, and the same byte code can be moved to a system with a Java chip on it, where the byte code is in fact compiled code which executes directly on the hardware.

Tokenized byte code is sort of a halfway point between interpreted and compiled.

---

### Post by aubertinsylvain on 2018-10-17
To sp40140. I am not glad to tell you that I tried a python file using many tabs, with vim, and tell you that tabs don't work well. First I used "softtabstop=4". I had to replace tabs by spaces. If you never had that problem, please tell me. Thanks

---

### Post by aubertinsylvain on 2018-10-17
Here is my file:
```
def silly(n, x):
    m=n
    stack = [iter(range(m))]
    total=0
    while stack:
        try:
        i = stack[-1].__next__()
        except StopIteration:
            stack.pop()
            continue
        total += i
        if total >= x:
            break
        if i ==  5:
            m -= 1
            stack.append(iter(range(m)))
    return total


print(silly(1,2))

~                                                                               
~                                                                               
"new2.py" 21L, 332C written                                   6,12          All
```

---

### Post by TheFu on 2018-10-17
You are missing the first line which tells the shell which interpreter to use.
The script must be marked as executable in the file permissions and it must be readable by any userid you want to allow execution.  Scripts that can't be read, cannot be run.  755 permissions for the file are fine.

Also, whenever posting 'code', please use code tags so things line up; critically important for languages like python where indentation matters! My signature has instructions.

---

### Post by aubertinsylvain on 2018-10-17
@TheFu  Please give me this precious first line, which I guess begins wiyh #!  Iam on linux and vim. Thanks

---

### Post by TheFu on 2018-10-17
I don't know your system, so things may be setup differently.  The first line for a python developer is specific to their setup.
[https://www.oreilly.com/library/view/python-for-unix/9780596515829/ch01.html](https://www.oreilly.com/library/view/python-for-unix/9780596515829/ch01.html) has examples for a few different scripting languages and a "general answer" for python, but it might not be what you want.

I'm a perl programmer and I don't use the built-in system perl for a number of reasons.  My programs currently use
```
#!/home/thefu/perl5/perlbrew/perls/perl-5.26.0/bin/perl
```
Because I want to use version 5.25.0 of perl.

If I manage my environment, I can use
```
#!/usr/bin/env perl
```

If I use perl6 instead of perl5, the answers would be different.
If I want to use the system perl, which I never want, but if I did, it would be 
```
#!/usr/bin/perl
```
This is perl v5.22.1, not what I want.

Clear as mud?

And the editor doesn't matter for this line. Never will.

---

### Post by oldfred on 2018-10-17
I have only used geany for python. But first thing I do is change defaults to replace tabs with spaces. I think both editing & projects & saved files settings all need changes.

I used to use this, but that defaulted to python2:
#!/usr/bin/python

I have used these and someone posted one was better than other, but forgot why?
#!/usr/bin/python3
#!/usr/bin/env python3

---

