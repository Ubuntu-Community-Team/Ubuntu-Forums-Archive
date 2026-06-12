---
title: "Bug?  I can type in 3 characters into the terminal and it performs a sudo command..."
date: 2014-06-26
forum: General Help
---

### Post by hot.sauce.jake on 2014-06-26
I was made aware of this problem because I pressed the up arrow in the terminal so that I could see my previous command (of course it didn't work).  Turns out there was a section that said:

```
sudo apt-get install pommed
```

when I know I didn't type that.  To test, part of the string I entered into the terminal had

```
!35
```

missing from it.  When I type that into the terminal and press enter (or tab) it runs that command!  Am I missing something here?

I already have pommed installed from installing Ubuntu on my Macbook Pro 4,1... I've had this install roughly 6 months now.


=====================

In one sentence: When I type "!35" in the terminal and press enter it runs the command "sudo apt-get install pommed"

---

### Post by papibe on 2014-06-27
Hi hot.sauce.jake.

It is definitely not a bug.

You are calling bash's history.  You can read all about it if you run:
```
man history
```
and then jump to the section called 'Event Designators'.

Hope it helps. Let us know if you have more questions.
Regards.

---

