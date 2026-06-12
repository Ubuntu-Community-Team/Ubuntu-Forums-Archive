---
title: "Large files extraction"
date: 2007-03-30
forum: General Help
---

### Post by Gryphin on 2007-03-30
Hi!
I looked everywhere and I can't find information how can i extract zip files larger than 2GB. I can remember I needed special command in terminal but I can't remember what it looked like nor what archiving programs it involved:(

---

### Post by spin2cool on 2007-03-30
From what I understand, you can either download the source and recompile unzip with large file support turned on, or use another utility like 7zip to handle the file.   google around for more detailed info

---

### Post by Gryphin on 2007-03-30
gzip, 7zip and other archivers from ubuntu's repos doesn't seem to work

---

### Post by acormack on 2007-03-30
Do you know what program was used to create the zip inthe first place?

---

### Post by Gryphin on 2007-03-30
Nope, I don't

---

### Post by acormack on 2007-03-30
According to [http://www.info-zip.org/FAQ.html](http://www.info-zip.org/FAQ.html)

the zip file itself should be able to go to to 256TB but no single file should be over 4GB

How big a file do you need to zip/unzip?

---

### Post by fdrake on 2007-03-30
are you sure it is a zip file or it's not corrupted, what does this command says:
file name.zip

---

### Post by Gryphin on 2007-03-30
My zipped file that I need to be extracted is 2.3GB.

---

### Post by acormack on 2007-03-30
what does the output of unzip -t {filename} look like?

---

### Post by Gryphin on 2007-03-30
> **acormack said:**
> what does the output of unzip -t {filename} look like?

...
 testing: data1.cab                OK
    testing: data1.hdr                OK
    testing: data2.cab               
  error:  invalid compressed data to inflate
....

I had the same problem few moths ago and downloaded the file few more times getting the same error when trying to extract. I remeber i've found a way to extract large files and it worked. Now I can't remember what the way was neither where was it posted :(

---

### Post by acormack on 2007-03-30
I am almost certain you have a corrupt zip file.

I suggest making a copy first then you could try to fix it with zip -FF {copyfilename}

Alec

---

### Post by fdrake on 2007-03-30
[http://www.experts-exchange.com/OS/Linux/Q_21191434.html](http://www.experts-exchange.com/OS/Linux/Q_21191434.html)  - similar problem
did you try this in a windows machine??

---

### Post by Gryphin on 2007-03-30
[http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=803569&admit=-682735245+1175289620486+28353475](http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=803569&admit=-682735245+1175289620486+28353475)

I think I found solution. The last post says:

 I have find a solution for a zip archive file with a single 2.5Gb file using -p option

unzip -p a.zip > x

I do not know what he meant, yet, I'm gonna try that -p option and see if it works.

---

### Post by acormack on 2007-03-30
I suggest making a copy of the zip

then trying to fix with 

zip -FF copyzipname

---

### Post by Gryphin on 2007-03-30
zip -FF:
zip error: Missing or empty zip file 
now I am completly confused :/

---

### Post by acormack on 2007-03-30
Just in case it was a file permission problem can you please try

sudo zip -FF filename.zip

p.s.  Is it possible to get another copy of the zip and see if that works?

---

### Post by Gryphin on 2007-03-30
Well... It is possible, but it's 2,3GB so it's quite a few hours of downloading. I did downloaded it few times last time I had this error (it was in January if I remember well) and the problem appeared to be in extracting method not in file corruption. That's why I started to look for that solution and not trying to download that huge file again.

sudo zip -FF gives the same resoultat as zip -FF :(

---

### Post by acormack on 2007-03-30
if you type md5sum filename.zip you will get the md5 hash

You could compare that with the one on the original server if it is published.

That might tell you if the file is corrupt.

---

### Post by spin2cool on 2007-03-30
Recompliling unzip from source with these flags enabled may do the trick:

[http://bugs.centos.org/view.php?id=1382](http://bugs.centos.org/view.php?id=1382)

---

