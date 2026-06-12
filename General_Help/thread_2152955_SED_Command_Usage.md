---
title: "SED Command Usage"
date: 2013-06-09
forum: General Help
---

### Post by CosmicFlux on 2013-06-09
Hi,

I've looked around Google and the Sed man page, but I still can't figure out where I'm going wrong. 

I have a config file with the line **variable=filename** and I'm trying to replace that line using sed in a script, like so:

**sed -e 's/variable=filename/variable=newfilename/g $HOME/inputfilename**

It's not working though. The file remains unchanged. 

I'm clearly missing something!


Cosmic

---

### Post by steeldriver on 2013-06-09
'sed' streams any output (including any substitutions it makes) to stdout by default - to make changes to a file 'on the fly' you will need the -i (interactive) flag

```
$ sed **-i** -e 's/variable=filename/variable=newfilename/g' $HOME/inputfilename
```

Just fyi, people seem to just throw the 'g' modifier in for good measure but really it is only necessary if you are trying to change more than one instance per line

---

### Post by CosmicFlux on 2013-06-09
Thanks!

It's still not working. Could it be that the filename contains an underscore?


Cosmic

---

### Post by Cheesemill on 2013-06-09
You're missing a ' after the /g in your first post...
```
sed -e 's/variable=filename/variable=newfilename/g**[COLOR=#ff0000]'[/COLOR] **$HOME/inputfilename
```

---

### Post by CosmicFlux on 2013-06-09
Sorry, just a typo. Here's the actual code from the script:

```
sed -i -e 's/Greeter=LinuxTermOS_Default.xml/Greeter=LinuxTermOS_Orange.xml/'  $HOME/GdmGreeterTheme.desktop

```

Cosmic

---

### Post by Cheesemill on 2013-06-09
The full stop has a special meaning in regular expression syntax, to use it as a regular full stop you need to escape it...
```
sed -i -e 's/Greeter=LinuxTermOS_Default\.xml/Greeter=LinuxTermOS_Orange\.xml/'  $HOME/GdmGreeterTheme.desktop
```

---

### Post by CosmicFlux on 2013-06-09
Right, I've done that. Still no joy, though. I decided to create a test file containing a list of single words and run the command against that file, and it works perfectly. It just wont replace the line in the file I *want *to edit.

---

### Post by Cheesemill on 2013-06-09
Can you post a copy of the file along with the ***exact*** command you are running please, I need to take a closer look.

---

### Post by Vaphell on 2013-06-09
it should work either way because . in regex would match literal '.' either way. Besides in the second part of expression you don't need to escape anything.

OP, does that sed command print out the proper result to terminal?

---

### Post by CosmicFlux on 2013-06-11
Hey!

Turns out I had an uppercase 'S' when there should have been a lowercase one. Sed now works absolutely fine! Now I can use it to create shell functions for Linux TermOS.  

Thanks for your help.

---

