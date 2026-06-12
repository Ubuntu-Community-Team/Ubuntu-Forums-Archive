---
title: "This is how to find error messages reported during an upgrade."
date: 2014-10-09
forum: General Help
---

### Post by landstander on 2014-10-09
**_Description of problem:_**
After clicking on the update manager icon, a GUI (Graphical User Interface) with the option to see the updates output in an embedded terminal is shown. Inside this embedded window an error message scrolls by. For example it might be something about not being able to load a kernel module for an NVIDIA driver or something like that. This error message will in some or possibly most cases scroll by to quickly to see what it was, and there will most likely not be enough time to copy it down, and copy and past does not work from this embedded terminal window (as of the date of this post). The update manager will close this embedded terminal window as soon as the update is complete leaving you with no way to get whatever that error message was.

**_Questions you might be left with after the above situation:_**
1.) How can I locate the error message now that it is no longer available in the embedded terminal window of the update manager?
2.) (This is probably the same question as #1 but...) Where are the log files for the updates kept on the system?

**_Answers to the above questions and how to solve the problem:_**
A google search for "Ubuntu update log" returns the answer:
[http://ubuntuforums.org/showthread.php?t=1004326]("http://ubuntuforums.org/showthread.php?t=1004326")
The above thread explains where to find the update log if you used the GUI for the update manager via an update icon somewhere on your system (see: "Summary" below).
_Note in case you didn't know:_ You can also do updates from the CLI (Command Line Interface) via "sudo apt-get update".

**_Summary:_**
To find the update log for a system update do one of the following:
**1.)** _CLI method:_
```
cat /var/log/apt/term.log
```

**1.a.)** _Alternate command line method showing only lines containing the word error:_
```
cat /var/log/apt/term.log | grep error
```

You could also use "awk" or "sed" instead of "grep" on the above line and as long as you give awk or sed the appropriate command line arguments (see: "man sed" or "man awk" from the command line). With "awk" or "sed" you can parse the output of the "term.log" file to give you a more complete or relevant list for whatever you are searching for in that document. The man pages can be a bit cryptic so you may wish to augment that resource with tutorials found via a search engine (ixquick or duckduckgo are good alternatives to google).

**1.b)** _Alternative CLI method showing the line containing the case insensitive word "error" and the line following that found word using "sed":_
```
cat /var/log/apt/term.log |sed -n '/error/I{N;p}'
```

**1.c)** _Alternative CLI method showing the line containing the case insensitive word "error" and the line following that found word using "awk":_
```
cat /var/log/apt/term.log |awk 'BEGIN {IGNORECASE=1} /error/{print; getline; print}'
```

**2.)** _GUI method:_
Open up your favorite text editor and from there open the file "/var/log/apt/term.log" then use your text editors search functions to find whatever error message you were looking for. :)
For example, in Ubuntu press "alt+F2" then enter the following:
```
gedit /var/log/apt/term.log
```

Hope this helps. :)

**_Notes about why I posted this:_**
1.) When clicking the "Check If Already Posted" button after entering the subject line for this post, the search returned no results.
2.) It took a lot of research and trial and error to find all the relevant information and compile it into this single post (especially the parts about sed and awk).
3.) It took more then a few search engine searches to find all the relevant information.

---

