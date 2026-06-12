---
title: "[SOLVED] grep command does nothing?"
date: 2008-04-01
forum: General Help
---

### Post by Rytron on 2008-04-01
I am trying to use the grep command but nothing happens.
It is installed. I test it by creating a .odt file with the word sky in it, this is located on the desktop. I cd to the Desktop, run the terminal and type grep sky *.odt 
Then the cursor goes to the next line and nothing happens. Whats wrong here?
Thanks.

---

### Post by Arwen on 2008-04-01
I think we don't use it correctly but I've tried different things (from [here]("http://www.gnu.org/software/grep/doc/grep_13.html") ) which either gave me a bash or a continuous flow of symbols I can't understand.
When I type sth similar to "grep sky *.odt "  the output is (translated)
"Binary file sky.odt" doesn't match" .

---

### Post by dcstar on 2008-04-01
> **Rytron said:**
> I am trying to use the grep command but nothing happens.
It is installed. I test it by creating a .odt file with the word sky in it, this is located on the desktop. I cd to the Desktop, run the terminal and type grep sky *.odt 
Then the cursor goes to the next line and nothing happens. Whats wrong here?
Thanks.

An OpenOffice file is not a plain text file, "sky" does not exist in it in a format grep can match.

Do your tests with plain text files and it should work.

---

### Post by justleen on 2008-04-01
> **dcstar said:**
> An OpenOffice file is not a plain text file, "sky" does not exist in it in a format grep can match.

Do your tests with plain text files and it should work.


Working as designed, i'd say "))

---

### Post by majkiw on 2008-05-23
> **dcstar said:**
> An OpenOffice file is not a plain text file

If anyone was interested: .odt file is just an .jar archive containing mostly .xml files which describe document's content and styles.

So you would have to extract it prior to using grep ;)

---

