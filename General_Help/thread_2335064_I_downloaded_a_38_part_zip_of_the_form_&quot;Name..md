---
title: "I downloaded a 38 part zip of the form &quot;Name.zip.XXX&quot;, how do I unzip them?"
date: 2016-08-25
forum: General Help
---

### Post by johnbross on 2016-08-25
I downloaded a 38 part zip of the form "Name.zip.XXX", so there's "Name.zip.001" then "Name.zip.002" then "Name.zip.003" ...etc how do I unzip them using the terminal?

(Also they are protected by a password which I know, of course)

---

### Post by howefield on 2016-08-25
Extract the first zip part and it should find and extract the rest automatically.

---

### Post by johnbross on 2016-08-25
> **howefield said:**
> Extract the first zip part and it should find and extract the rest automatically.

I used this command: unzip MyName.zip.001 -d MyName, and I got 
  
End-of-central-directory signature not found.  Either this file is not  a zipfile, or it constitutes one disk of a multi-part archive.  In the  latter case the central directory and zipfile comment will be found on  the last disk(s) of this archive. 

By the way, how do I include the password in the command line?

---

### Post by HermanAB on 2016-08-25
It may have been broken up with 'split'.  So try using 'cat' to concatenate them all into one big file, in numerical order and then try using gzip.

---

### Post by johnbross on 2016-08-27
> **HermanAB said:**
> It may have been broken up with 'split'.  So try using 'cat' to concatenate them all into one big file, in numerical order and then try using gzip.

Which command do I have exactly to use? THanks

---

### Post by howefield on 2016-08-27
```
cat MyName.zip.* > nameofnewfile.zip
```

Assuming that you are in the folder that contains the files, or use the path to them if you are not.

---

