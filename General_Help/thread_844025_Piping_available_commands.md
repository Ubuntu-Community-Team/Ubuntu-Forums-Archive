---
title: "Piping available commands"
date: 2008-06-29
forum: General Help
---

### Post by QuacoreZX on 2008-06-29
Hey all,

This is more of a linux-in-general question than an ubuntu question, but I'm sure the majority of you know about piping and regular expressions via terminal.  As you know, pressing <Tab><Tab> will display a list of all known available commands in terminal, one per line, but unfortunately this is an interactive command and therefore unable to be piped.  Anyone know of an alternative to it so I can pipe and search for something in specific with grep?

---

### Post by conscious on 2008-06-29
May be this?
[http://www.gnu.org/software/bash/manual/bashref.html#Programmable-Completion-Builtins](http://www.gnu.org/software/bash/manual/bashref.html#Programmable-Completion-Builtins)

---

### Post by ghostdog74 on 2008-06-29
> **QuacoreZX said:**
> Hey all,

This is more of a linux-in-general question than an ubuntu question, but I'm sure the majority of you know about piping and regular expressions via terminal.  As you know, pressing <Tab><Tab> will display a list of all known available commands in terminal, one per line, but unfortunately this is an interactive command and therefore unable to be piped.  Anyone know of an alternative to it so I can pipe and search for something in specific with grep?

usually , commands can be found in /usr/bin, /usr/sbin, /usr/local/bin. some in /opt if you installed third parties. what exactly do you need to find? 
```

find /usr -name "somecommand" -print

```

---

### Post by QuacoreZX on 2008-06-29
Not looking for anything in particular, but sometimes I can come up with a gist of what a command name is, but not all of it.  Just looking for a simple solution to a simple problem.

---

### Post by ghostdog74 on 2008-06-29
you can use man -k <keyword>
eg man -k hardware
to search for commands.

---

### Post by sdennie on 2008-06-29
You could use script to capture the output of the <Tab><Tab>:

```

script
<Tab><Tab>
*Hold down spacebar for a while*
exit

```

To clean up the output:

```

cat typescript | sed -e s/--More--// | sed -e s/\\r//g > output

```

That should create a file called output that would be close to the equivalent of redirection <Tab><Tab>.

Hope that helps.

---

### Post by ghostdog74 on 2008-06-29
> **vor said:**
> 
```

cat typescript | sed -e s/--More--// | sed -e s/\\r//g > output

```


```

sed -e s/--More--// -e s/\\r//g typescript 

```

---

### Post by sdennie on 2008-06-29
> **ghostdog74 said:**
> ```

sed -e s/--More--// -e s/\\r//g typescript 

```

Surely with the links in your signature you are familiar with TIMTOWTDI ("There's more than one way to do it").  ;)

---

### Post by ghostdog74 on 2008-06-29
> **vor said:**
> Surely with the links in your signature you are familiar with TIMTOWTDI ("There's more than one way to do it").  ;)
yes, indeed. However, more than 1 way doesn't mean those ways are more proper, efficient, neat and simple. It pays to eliminate extra redundant code whenever possible.

---

### Post by sdennie on 2008-06-29
> **ghostdog74 said:**
> yes, indeed. However, more than 1 way doesn't mean those ways are more proper, efficient, neat and simple. It pays to eliminate extra redundant code whenever possible.

I'll not get into a long argument about this but:

1) People get into habits and those habits are often good.  Starting with cat and ending with a redirect to a different file is logical, clean and insures you aren't clobbering the original file.

2) Your command doesn't provide a record of the output.  It just prints the output to the screen.  You need to redirect to output or have sed edit the file inline.

---

### Post by ghostdog74 on 2008-06-29
> **vor said:**
> I'll not get into a long argument about this but:
me too. Just showing you how its done properly.

> 
1) People get into habits and those habits are often good.  Starting with cat and ending with a redirect to a different file is logical, clean and insures you aren't clobbering the original file.

If you have not known about UUOC, start [here]("http://www.google.com.sg/search?hl=en&q=UUOC&btnG=Google+Search&meta=").
most utilities you use, sed/grep/awk/wc etc, all are able to take in input file. So there's really no need to use cat or piping to sed 2 times, which is just wasting processing time. 

> 
2) Your command doesn't provide a record of the output.  It just prints the output to the screen.  You need to redirect to output or have sed edit the file inline.
its as easy as adding -i to it if the version supports it. Otherwise redirection would do. trivial. No arguments about that and nothing related to code redundancy.

---

### Post by sdennie on 2008-06-29
> **ghostdog74 said:**
> me too. Just showing you how its done properly.

In that vein:

> **ghostdog74 said:**
> usually , commands can be found in /usr/bin, /usr/sbin, /usr/local/bin. some in /opt if you installed third parties. what exactly do you need to find? 
```

find /usr -name "somecommand" -print

```

Is an inefficient and ambiguous way to write:

```

which somecommand

```

> 
If you have not known about UUOC, start [here]("http://www.google.com.sg/search?hl=en&q=UUOC&btnG=Google+Search&meta=").
most utilities you use, sed/grep/awk/wc etc, all are able to take in input file. So there's really no need to use cat or piping to sed 2 times, which is just wasting processing time.


Again, people get into their own habits.  Catting something to a chain of pipes seems logical to me and many others.  It doesn't matter if it seems useless.

---

### Post by ghostdog74 on 2008-06-29
> **vor said:**
> In that vein:



Is an inefficient and ambiguous way to write:

```

which somecommand

```


you can use which, but only when the command you want to find is in one of the directories in your $PATH variable. 

> 
Again, people get into their own habits.  Catting something to a chain of pipes seems logical to me and many others.  It doesn't matter if it seems useless.
Certainly. you are entitled to that. Its easier to pick up good habits from the start than break old ones. [For your reading pleasure]("http://groups.google.com.sg/group/comp.unix.shell/browse_frm/thread/532d7fa8734bc588/a57454b9911e1fc6?hl=en&lnk=gst&q=Useless+use+of#a57454b9911e1fc6")

---

