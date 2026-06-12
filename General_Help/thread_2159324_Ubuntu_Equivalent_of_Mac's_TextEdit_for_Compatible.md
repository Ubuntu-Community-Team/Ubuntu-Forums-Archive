---
title: "Ubuntu Equivalent of Mac's TextEdit for Compatible Program Use"
date: 2013-07-02
forum: General Help
---

### Post by Redvyper on 2013-07-02
Hello all,

Please excuse me if this post is in the wrong place or is vague (I'm bit of a new user to Ubuntu). I am running v13.04 and trying to run a specialized piece of software that was originally designed for Snow Leopard (but should work fine on Ubuntu). The program uses another program called "MAST" (Motif, Alignment, and Search Tool - [http://meme.nbcr.net/meme/](http://meme.nbcr.net/meme/) ). The MAST is supposed to output three files every time it is ran: xml, html, and a text. However when I run it on Ubuntu, it does not output the text file. When ran on a fellow's Mac, it outputs a text file just fine. From our own bug checking we believe the issue is that MAST relies on Mac's TextEdit software to output its text file.

Is there any potential way of working around this (it's absolutely necessary that it outputs this text file) that doesn't involve changing MAST's source code? Like changing Ubuntu's/the terminal's default text editor that functions similarly to Mac's TextEdit?

What other information should I provide?

For the curious: I am doing research work on DNA motifs and trying to get another colleague's program suite (uses MAST) to work on my laptop. This program, MAST, *is* Linux compatible but the version I have to use is from 2010. 

Cheers,
redvyper

---

### Post by tgalati4 on 2013-07-02
*gedit* would be an equivalent program.  Perhaps there is a configuration file that you can change the default text editor.

---

### Post by Redvyper on 2013-07-02
My Ubuntu uses *gedit *as its default text editor already.

My issue is similar to a past user's woes: [http://ubuntuforums.org/showthread.php?t=1856574](http://ubuntuforums.org/showthread.php?t=1856574)

However the main difference between his dilemma and mine is that he's making/editting a pre-existing text file. I am running a program through terminal that is supposed to automatically made dozens of these text files.

---

### Post by tgalati4 on 2013-07-03
It could simply be an encoding problem UTF8 versus Latin vs Western character encoding.  I thought that the Mac used UTF8 as does Ubuntu, but it is possible that the Mac is set to a different character encoding.  Also, check the language settings of both operating systems.  A language difference could result in strange characters.

---

### Post by 3rdalbum on 2013-07-03
I disagree with your analysis- I really doubt this program depends on any text editor in order to output text.

Does the program appear to run when you start it? Does it give you any error messages? Are you running it with the correct command-line parameters or configuration file settings to create those files?

Another potential issue is that, typically old software doesn't work well on new Linux distros. The pace of Linux development is so quick that your program from 2010 might not be compatible with any distros made after 2010.

Why wouldn't you use the newest version?

---

### Post by Redvyper on 2013-07-03
The program runs fine and will even output the information I want in the terminal it self. It just won't output to a textfile - no error is given. The later versions of MEME don't come with MAST. I'm not sure why the development group stopped updating/including MAST in its updated versions.

---

### Post by steeldriver on 2013-07-03
> **Redvyper said:**
> The program runs fine and **will even output the information I want in the terminal it self**. It just won't output to a textfile - no error is given. The later versions of MEME don't come with MAST. I'm not sure why the development group stopped updating/including MAST in its updated versions.

would redirecting (or teeing) the terminal output to a file be a possible workaround for you?

---

### Post by Redvyper on 2013-07-03
> **steeldriver said:**
> would redirecting (or teeing) the terminal output to a file be a possible workaround for you?

The program automatically produces 8-20 of these text files at a time and then is supposed to re-read the data with the results of the text files in mind, and then re-evaluate the data in the text files. It's a recursive process that's done on large data sets. I'm not sure how I would redirect the terminal output to a text file in an efficient manner.

> **3rdalbum said:**
> I disagree with your analysis- I really doubt this program depends on any text editor in order to output text.
 
Does the program appear to run when you start it? Does it give you any error messages? Are you running it with the correct command-line parameters or configuration file settings to create those files?

Another potential issue is that, typically old software doesn't work well on new Linux distros. The pace of Linux development is so quick that your program from 2010 might not be compatible with any distros made after 2010.

Why wouldn't you use the newest version?

So your message motivated me today to go against my colleague's original instructions and just downloaded the newest version, wa-la - it works. I feel dumb now. Thank you.

---

