---
title: "How to automatically rename files when saving?"
date: 2008-03-09
forum: General Help
---

### Post by themightymegatron on 2008-03-09
Hi guys. I'm not sure exactly which forum this should go in, so I figured General Help would be my best bet. I'm wondering if there's a way to configure Ubuntu to automatically rename files when saving them. For example, since the terminal can't read spaces in file names, and the idiots at Microsoft couldn't make Windows conform to good standards so people might learn to name files for easy access in a command line, a lot of the files I download online (pictures, text, you name it) have spaces in the file names. Is there maybe a config option in Ubuntu or at least a script that someone knows of that I could use to either set Gutsy to auto rename files or run the script from BASH so it would rename all the files in a particular directory, removing spaces in favor of underscores or hyphens? I've looked all over the forums and google and yet she gives me nothing :(

For clarity, I'm running Gutsy 7.10, and I've only been using Linux for about 3 months now, but I feel like I've picked up enough to use it at a level maybe a little over beginner, haha. Thanks again guys, I appreciate all answers.

---

### Post by raul_ on 2008-03-09
I think you can read spaces, adding a "\<space>" like this:

```
[raul@horus ~]$ ls
cacert.crt  Desktop  Downloads  Faculdade  Imagens  this is a test
[raul@horus ~]$ cd this\ is\ a\ test/
[raul@horus this is a test]$ 
```

---

### Post by StOoZ on 2008-03-09
> **raul_ said:**
> I think you can read spaces, adding a "\<space>" like this:

```
[raul@horus ~]$ ls
cacert.crt  Desktop  Downloads  Faculdade  Imagens  this is a test
[raul@horus ~]$ cd this\ is\ a\ test/
[raul@horus this is a test]$ 
```

yes you are right, its called 'escape character'. =D>

---

### Post by themightymegatron on 2008-03-09
> **raul_ said:**
> I think you can read spaces, adding a "\<space>" like this:

```
[raul@horus ~]$ ls
cacert.crt  Desktop  Downloads  Faculdade  Imagens  this is a test
[raul@horus ~]$ cd this\ is\ a\ test/
[raul@horus this is a test]$ 
```

Aaah, I see. Thank you very very much! Worked like a charm!

---

### Post by raul_ on 2008-03-09
> **themightymegatron said:**
> Aaah, I see. Thank you very very much! Worked like a charm!

Tab completion also does the trick

---

