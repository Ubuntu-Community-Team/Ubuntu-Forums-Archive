---
title: "buffer problems / display capabilities"
date: 2005-10-11
forum: General Help
---

### Post by raspa_sete on 2005-10-11
I have a portuguese keyboard, but in general I read stuff in portuguese, english and german. my problem is that the my console doesn't recognize the characters with the accents (for instance ä, ö, ü, á, ã on so forth).

I can write these characters in the gnome-terminal, but when I do an ssh to some server, the files I browse there have lots of problem with the accentuation (but on other computer everthing is fine, so problem is my PC).

does anyone know how to solve this?

(in this server that I use the following character-set ISO-8859-1) but where do I change this in my ubuntu?

and I get this stange behavior from the shell, so when I do a "á" the shell see's it as two characters and so when I do backspace I can go two spaces back (I can even erase the prompt line)
how can I correct this?

---

### Post by heimo on 2005-10-11
Not sure if this will help, but I'd try to:
```
sudo dpkg-reconfigure locales
```

---

### Post by raspa_sete on 2005-10-11
I think that should do the trick, but have you any idea of the difference between

pt_PT ISO-8859-1 and pt_PT.UTF UTF-8

the pt_PT, is the language followed by the variant (portuguese from portugal). I supose that ISO and UTF are two different types for aASCII table or something.

which one should i choose?

---

### Post by heimo on 2005-10-11
UTF8 and ISO are different character encodings / sets. I always prefer ISO8859-15 (includes scandinavian characters and euro sign), but that's mainly a habbit - I don't have any real arguments.

Run *locale *to see your current settings. For me 'POSIX' doesn't work, but fi_FI is ok. (The "special" characters Finns/Swedes use: &#229;&#228;&#246;)

---

### Post by raspa_sete on 2005-10-11
thanks, it's now solved!
I ended up by installing the portuguese, finnish (from finland???), german.
I odnt only get the euro simbol in the console, but I have en_US. going to get the new one and all should be fine.

thanks again

---

