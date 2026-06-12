---
title: "Sending music through pipes"
date: 2012-11-22
forum: General Help
---

### Post by rickybobby7 on 2012-11-22
Hey everybody, I'm new to this forum and there's a question about pipes I want to ask. 

The idea of piping things through the system seems amazingly powerful to me, but most info on it I can find online is sparse. So I thought it would be good to invent a project to force myself to learn. 

I would like to enter a song in the terminal (e.g. "Beethoven's Seventh Symphony, Movement No. 2"). Then I'd like to send this data to my web browser which will find the most relevant link to download. Upon downloading, I want the information imported into iTunes, which will then sync it to my phone through wi-fi. 

I do this routine all the time, whenever I download new (obviously free and legal, of course :-\" ) songs. I'd love to automate it, and I think it would be good practice in learning how to send information through the system. 

TL;DR: I'm trying to automate data transfer of songs-- Can any veterans tell me if this is practical, and if so where to begin? (Or if this is not the right place to ask, where I should ask?)

Thanks!

---

### Post by Aaron Christianson on 2012-11-22
That isn't exactly how Unix pipes work. Pipes generally just pipe the text output of one command into the input of another. This is a very powerful feature once you get to know several terminal commands, but it doesn't really have anything to do with syncing media across devices. Many GUI applications can't be scripted like this because they are not really designed to receive extensive input from the command line, unfortunately. This is one of the reasons many experienced linux/unix geeks prefer command line tools; because, while they are not pretty and may be somewhat difficult to learn at first, they can be combined with any other terminal command via pipes; this is the kind of power and versatility that gui apps just can't offer.

However, this does not mean that what you are trying to do is impossible. It just means that it isn't a job for unix pipes per se.

First of all, typing the name of a song and automatically finding the best result is rather unlikely. This will require some user interaction, unless you are a brilliant programmer who can write a program that will automatically parse websites and find the best download link. I doubt you are that kind of programmer, and I certainly am not, nor would I be willing to take the time to write such a sophisticated algorithm just to help some schmo on a forum.

Your brain is much smarter than a computer, and you are going to have to find the best download link. There are several things you might be able to do, however, to narrow it down.

You could search torrent sites like a normal person (torrentz.eu is nice, though for legal purposes, it should only be used to obtain public domain or otherwise freely distributable music. derp). There are also several programs you can use to search for torrents without opening your browser, but I will leave it to you to search for them in the software center.

Some torrent clients can be set to automatically begin downloading torrent files saved to a certain directory or whatever.

Another possibility, especially if you are more interested in doing one song at a time, would be to find a utility that can download online videos (only videos that explicitly use an open license like creative commons are legal to download). It is against forum policy to give directions on downloading youtube videos, but again, I believe there are items in the software center that can do things like this. Not sure. I'm actually on Arch, but we have tons of stuff that gets the job done. You will have to figure out how to do that elsewhere, unfortunately.

Anyway you will want to make sure your media eventually makes it into some kind of target directory, which can usually be automatically chosen by the program that gets it for you. From there it would be relatively easy to write a script that will scan the folder for certain types of files. If you get a video file, you can have the script use ffmpeg to automatically re-encode the video to .flac or another good format (flac is the best for something like this though). Once you have the media in the correct format, you could have it automatically copied to a directory where iTunes will scan for it (no idea how you got itunes working on Linux, but props). At the same time, you could copy it to some kind of cloud folder like Dropbox or Ubuntu One. Both of these cloud services can be accessed on iPhone or Android, though there are certain security hazards of using a third-party cloud service. On the other hand, if you just want it on your home wifi service, you can use something like an ftp or samba share to make the files available to your phone.

It's not the same as a pipe, but you can still automate a lot of this workflow by other means (including shell scripts). Once you figure out how you are going to obtain your media, I or someone else can help you figure out how you are going to get it where you want in, in the file formats you want it, though I haven't used iTunes in ages personally, and cannot necessarily give you application specific advice for it.

This is a fair amount of work to set up, however, especially if you plan on doing a local media server.

---

### Post by rickybobby7 on 2012-11-22
Thanks for the help, Aaron!

Your advice is very practical, in suggesting that I weave together existing tools to achieve my end goal. But my biggest end is simply control over the system. Why is it exactly that the command line can't control GUI apps? Is this impossible in principle, or just in practice (because the GUI apps are written as binaries, not text files, or something like that)? 

Because we ultimately never interact *directly* with a GUI anyway, right? We talk to the OS and the OS talks to the GUI. So why shouldn't there exist some mapping between precise CLI instructions and GUI operations, through the medium of the OS?

Okay, so maybe the process of selecting songs requires some human intellect. But the rest of the process is mindless, and (though I am a Linux newbie) my gut tells me that everything mindless can (and should, time permitting!) be automated. Are there any big errors in this line of thinking?

Best,
rickybobby7

---

### Post by Vaphell on 2012-11-22
> Why is it exactly that the command line can't control GUI apps? Is this impossible in principle, or just in practice (because the GUI apps are written as binaries, not text files, or something like that)? 

command line communicates with program using text parameters and if some functionality requires 'click here, type that, mark checkbox there' and that functionality is not exposed in some way for command line use, it becomes extremely hard to achieve the effect programmatically.
There are tools that allow to move mouse and generate keypresses and mouseclicks which could be used to create rudimentary macros (move mouse there, click). Ultimately these macros would be very fragile, as without eyes they would shoot in the dark, they might click things that don't exist and they would never react to visual feedback. Of course 'artificial eyes' are possible, visual processing techniques exist, after all there are bots that can play games but it's even bigger can of worms.
TL;DR: automating gui programs is hard and you should find some command line tools that offer the functionality. KISS principle in action ;-)

> Okay, so maybe the process of selecting songs requires some human intellect. But the rest of the process is mindless, and (though I am a Linux newbie) my gut tells me that everything mindless can (and should, time permitting!) be automated. Are there any big errors in this line of thinking?

your line of thinking is certainly sound.
Create a list of specific steps required to achieve your goal. Attack each step individually. Once you have these stages figured out, scripting them is trivial.

---

### Post by rickybobby7 on 2012-11-22
Thanks for the help, Vaphell!

You answered a lot of the questions I'd been thinking about. :)

---

### Post by Aaron Christianson on 2012-11-22
> **rickybobby7 said:**
> Why  is it exactly that the command line can't control GUI apps? Is this  impossible in principle, or just in practice (because the GUI apps are  written as binaries, not text files, or something like that)? 
Eh, it does have to do with text and binary stuff, but not exactly in the way you put it. The command line, at it's core is simply a mechanism for launching programs. It is up to the program itself, rather than the command line, how the user is allowed to interact with the program. This is why many experienced linux and unix user prefer tools that provide as many options as possible from the command line itself (stdin), and provide useful output text to the terminal (stdout). These are the kinds of programs that are useful with pipes and the best for automating.

Some  gui apps actually can be controlled from the command line, and most  will take at least one or two arguments, but it depends on the program.  For example, you can see which command line options firefox takes with this command ```
$ firefox -h
```There are a fair number of options, but the main problem is that, while you do have a degree of control over firefox from the command line, it isn't anywhere near enough to search for media or open relevant links. Furthermore, firefox provides almost no useful output to the terminal (well it does debugging messages, but not enough to really know what is going on with content).  This means it is basically impossible to write a script that will interact with content in a firefox window.

There are a couple of solutions. One would be to write a firefox js plugin that would send the information you wanted back to stdout. Another would be to use a browser that is designed to interact with the shell more directly like uzbl.

However, you don't really need a browser at all to locate and download media. There are already command line utilities for just such a purpose. 

> Because we ultimately never interact *directly* with a GUI anyway,  right? We talk to the OS and the OS talks to the GUI. So why shouldn't  there exist some mapping between precise CLI instructions and GUI  operations, through the medium of the OS?So, the kernel gets the info from the hardware and passes it along to the X server. The X server passes that info along to active windows and applications. There is a program called xdotool that allows you to send signals such as key presses and mouse movement and whatever to the X server through the command line. You are welcome to try and control your browser with this program, but I don't think you'll have much success.

Again, it isn't really necessary, because command line tools exist to do almost any task that a gui app can (except for tasks that really require eyes connected to a brain). If you want to leverage the power of unix, command line tools are simply the way it is done. In fact, many Linux gui apps are simply front-ends to command line utilities, but if you you want to automate them,  you need to use the utilities themselves, rather than gui front-end.

It is not impossible, but as a programmer, it is much easier, and far more tools are available for parsing text information than trying to parse information from the window server in order to control a gui app.

It's not that the programs themselves are text or binary (many cli apps are binaries, and some gui apps are plain text scripts). It's that programs useful to shell scripts take text input and generate text output. What we are talking about is basically at the core of what Unix is:

*Doug McIlroy then head of the Bell Labs CSRC and contributor to Unix pipes summarised Unix philosophy as follows:*[INDENT] *This is the Unix philosophy: Write programs that do one thing and do it well. Write programs to work together. Write programs to handle text streams, because that is a universal interface.*

[/INDENT]- from [http://en.wikipedia.org/wiki/Unix_philosophy](http://en.wikipedia.org/wiki/Unix_philosophy)
  
> Okay, so maybe the process of selecting songs requires some human  intellect. But the rest of the process is mindless, and (though I am a  Linux newbie) my gut tells me that everything mindless can (and should,  time permitting!) be automated. Are there any big errors in this line of  thinking?
Vaphell's comment is completely correct. You need to divide the task into steps and figure out which command line utility is needed to accomplish each step. From there, many of the people here can help you put together a script that will pipe them all together for your. It would be a great learning experience.

---

