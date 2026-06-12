---
title: "Correct line drawing in PUTTY"
date: 2007-04-25
forum: General Help
---

### Post by plafuro on 2007-04-25
Hi all,

I had some issues with line drawing when accessing my linux box from work. I found the following workaround in [this site]("http://www.wlug.org.nz/PuTTY"):

To make it all work right, you need to twiddle the following configuration settings:

Terminal &#8594; Keyboard:

    Change the sequences sent by: The Functions keys and Keypad:
        Select Linux.

Window &#8594; Appearance:

    Font settings:
        Pick a font that contains the Unicode line drawing characters, such as Andale Mono or Lucida Console. (Unfortunately Vista’s gorgeous new Consolas font does not have those.)

Window &#8594; Translation:

    Character set translation on received data:
        Select UTF-8.
    Adjust how PuTTY handles line drawing characters:
        Select Use Unicode line drawing code points.

Connection &#8594; Data:

    Terminal details: Terminal-type string:
        Enter “linux”.

Now line drawing characters should show up as they are supposed to.

---

### Post by mdeveaux on 2007-12-05
I also had do the following:
  Terminal -> Features
  check - Disable bidirectional text display

to get aptitude running correctly

---

