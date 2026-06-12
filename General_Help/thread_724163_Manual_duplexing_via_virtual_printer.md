---
title: "Manual duplexing via virtual printer?"
date: 2008-03-14
forum: General Help
---

### Post by run4flat on 2008-03-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/56444](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/56444) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Greetings all -

In short: I have a handy script that does some formatting for me (via pstops) and then prints, allowing for fairly simple manual duplexing.  Is there an easy way to create a virtual printer out of this script?

Now, for my long-winded post:

I have an idea and would appreciate any pointers to getting this to work.  I have written a really simple script which can take a pdf or ps file, split the odd and even pages, print the even pages in reverse, tell me to put the stack back into the tray, and finally print the odd pages in order.  This is how I accomplish duplexing without having to manually reorder the pages.  I know I could probably just wait for cups to come out with manual duplexing, but I actually have more complicated formatting in mind so it would be nice to have a more comprehensive solution.

It is my understanding that most programs (at least all of the programs I'll be using) send postscript commands to the driver which then does whatever processing is necessary before sending it to the printer.  Is this correct?  If so, it would be fantastic to be able to create a virtual printer called "HP Manual Duplexing" or some such thing so that I could reduce the number of steps necessary to create the finished double-sided document.  Presently I have to create a pdf or ps file and then run it through my script.

So here is my question: How can I turn my script into a virtual printer driver?

P.S.  Any solutions developed here could in principle work as solutions to the attached launchpad report, and could apply as a solution (or hack or whatever) for the brainstorm idea posted at [http://brainstorm.ubuntu.com/idea/3332/promote](http://brainstorm.ubuntu.com/idea/3332/promote).

---

### Post by run4flat on 2008-03-15
In all of my online research, I read somebody somewhere say, "Can't you just modify cups-pdf?"

Here's a breakdown of how all of the different elements of cups play a role (taken from the source tar.gz)

These are the C source files.  In what I originally suggested, I would (functionally) replace these with my script file.
> src/cups-pdf.h
src/cups-pdf.c

Next we have the contributions.  These are 
> contrib/cups-pdf-dispatch-0.1
contrib/pstitleiconv-0.2
contrib/SELinux-HOWTO
The pstitleiconv program converts internationalized titles to more suitable character sets for Windows file names and the cups-pdf-dispatch program can be used to automate emailing the final pdfs to various recipients.  If we decide to modify cups-pdf, THESE ARE OUR TARGETS.

Finally, we have the folder with the extra (i.e. essential) items:
> extra/cups-pdf.conf
extra/PostscriptColor.ppd

The configuration file is used by cups-pdf (not cups itself) and specifies the postprocessor.  The ppd file is a PostScript Printer Description file which, among other things, defines the user interface for teh printing dialog as well as the filter.  The PPD along with the compiled binary are the parts of cups-pdf that actually interact directly with cups.

So, what we can do if we like is create our own scripts and associated PPD file or create appropriate filter/postprocessing scripts that we plug into a copy of an existing printer driver.

I have also discovered the cupsfilter program, but I'm not sure that this will do what I'm looking for.

That's all I've got for now.  I'm going to fiddle with modifying an existing printer's filtering and postprocessing as well as explore cupsfilter since these appear to be the best ways to go.  I'll try to record my progress, but any ideas or words of wisdom would be greatly appreciated.

---

### Post by run4flat on 2008-03-15
I found another clue - in code form - to solving my problem.  If you're interested, see [www.g-loaded.eu/2006/12/03/pdf2email-cups-backend/](www.g-loaded.eu/2006/12/03/pdf2email-cups-backend/)

I feel like I've almost got this figured out.  I'll post a solution hopefully later today.

---

### Post by run4flat on 2008-03-17
So close and yet so far away.  For anybody interested in following, I'm mired in development issues, as discussed [here]("http://ubuntuforums.org/showthread.php?t=727107").  I'll post a solution when I've got it worked out.

---

### Post by arvs on 2008-04-06
Did you get any closer to a solution? I'm very much interested, since it's an issue I've long wanted to resolve (but don't know much about printing and scripts in Linux).

Also, does your script add a blank page when printing an odd number of pages (like my hp driver does in Windows) ?

---

### Post by run4flat on 2008-04-07
arvs -

You may have noticed I linked to a different thread about the backend getting information via GUI.  In principle I've solved the problem (and could get the manual duplexing backend working) but I'd like to make a more robust solution for the zenity daemon first.  Once that's up and running, I'll come back to manual duplexing since it should be trivial with an easy gui interface for the backend.

However, I have become engrossed in other things lately.  It's been on my mind and hopefully I will return to it within the next month or so.

Feel free to pester me or ask questions, though!  It might egg me on to get working on it sooner.  :]

---

