---
title: "An Interesting Problem/Challenge"
date: 2008-06-16
forum: General Help
---

### Post by frogitts on 2008-06-16
Here's something I want to do.

I have the CPU temp monitoring application logging CPU temperatures, for fun and research. I have a .ods OpenOffice spreadsheet set up to chart these logs.

All I have to do is open the log, select all, and copy. Then I open the spreadsheet (ChartThis.ods), select the first cell (A1) and hit paste, then hit enter on the import dialog to import it with the default options.

My question is, is there any way to automate this? Can I take the .log file (plain text) and add it to ChartThis.ods, preferably through terminal?

I'd love to schedule a task at the end of every day that takes that day's .log file and turns it into a spreadsheet with a chart.

---

### Post by Octagonal on 2008-06-16
maybe this?

[http://blogs.sun.com/wwalker/entry/keystroke_record_playback_for_testing](http://blogs.sun.com/wwalker/entry/keystroke_record_playback_for_testing)

I haven't used it but it sounds like it would work for what you're trying to do...

---

### Post by ad_267 on 2008-06-16
You could also save the log as a .csv file which is a plain text file with columns separated by commas and then OpenOffice.calc would open this as if it was a spreadsheet.

Edit: Sorry I didn't read the part about needing a chart, this won't be much use for that. You can probably write a macro to import the data and produce a plot. There should be some good tutorials out there on how to do this.

---

### Post by frogitts on 2008-06-16
This is a good start. As far as macros go, I've gotten a macro that can paste what I have in the clipboard, but I still have to open the .log file, copy the contents, open the ChartThis.ods file, run the macro, and hit enter to use the default importing options. Basically, recording the macro basically recorded only "paste the clipboard" and left the rest out. Personally, I'm not surprised.

What I'm really looking for is a bash script that I can use (or a script that I can turn into a Nautilus script, or something like that). What I think is possible is a script that would follow these steps:

1) Copy the contents of the current file (not the file itself)
2) Copy ./ChartThis.ods and rename the copy with the current file name -.log + .ods (to give it a unique filename).
3) Insert the contents of the clipboard into the new .ods file according to the default importing method of open office calc

I'm sure that the last step is by far the hardest, but I don't really know how to do the first two either. I can copy a file through bash and rename it, but I don't know how to copy the contents of the current file (although I can print them and put them into a new file through cat - this creates a useless .ods file though). I also wouldn't know how to grab the name of a file, subtract "log" and add "ods" onto the end of it.

And of course, if there were a way to paste cell contents into a spreadsheet through the terminal, that would just be cool. Can one call a macro in open office calc through terminal?

Edit: Looking at the macro tool in calc more and realizing just how powerful it is, I've realized that this may in fact be possible to do simply as a macro, using Calc to choose the file to import, though this is still not quite what I'm trying to do. I'll look more into this.

---

### Post by ad_267 on 2008-06-16
Ok this is how I would go about trying to do this but I don't really have the knowledge of the specific details.

1. Write a macro for OpenOffice that actually imports the log file rather than having to use the clipboard and creates the graph then saves this file with the current date.
2. Write a crontab that automatically runs openoffice in headless modes and runs this macro at a certain time every day.

Obviously doing this would involve a pretty good understanding of how to write macros in OpenOffice, although there may be example scripts out there that do a similar thing already.

Edit: Useful links
[http://www.oooforum.org/forum/viewtopic.phtml?t=2619](http://www.oooforum.org/forum/viewtopic.phtml?t=2619)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
I believe that running openoffice with the --headless option you would still need the "env DISPLAY=:0." in a crontab.

---

### Post by frogitts on 2008-06-16
How would you go about running a macro in headless mode? I've read the man page (I know, not much, but still...), and I couldn't figure that one out.

Edit: just read the first link, which gives the answer to this question.

---

### Post by ad_267 on 2008-06-16
Yup so I think it would be something like this:

oocalc -headless -o /home/username/templog/CPU_Temp_`date +"%Y-%m-%d"`.ods "macro://yourmacro()"

---

### Post by ad_267 on 2008-06-16
If you write a bash script to do this and you need to create files with the same name but different extension, have a look at the basename command.

```
man basename
```

---

