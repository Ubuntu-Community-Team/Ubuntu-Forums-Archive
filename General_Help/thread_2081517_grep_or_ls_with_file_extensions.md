---
title: "grep or ls with file extensions"
date: 2012-11-07
forum: General Help
---

### Post by Kevin McCready on 2012-11-07
I'm trying to list all my .wav files.
When I do

ls -ltR /home/k/Documents |grep -i '.wav'

I get all my files with wav in them (not just .wav) files.

What am I doing wrong?

---

### Post by rnerwein on 2012-11-07
> **Kevin McCready said:**
> I'm trying to list all my .wav files.
When I do

ls -ltR /home/k/Documents |grep -i '.wav'

I get all my files with wav in them (not just .wav) files.

What am I doing wrong?

hi
1. man grep
2. that's what you want:  ls -ltR | grep -e *.wav
3. faster is: find . -name "*.wav"

but please read the man pages some times. command like find and (e)grep are very
powerful commands ( especaly when combined).

bye

---

### Post by Vaphell on 2012-11-07
> 2. that's what you want: ls -ltR | grep -e *.wav
this is wrong in 2 ways:
- *.wav will expand to the list of watever .wav files in current dir
- *.wav is not a proper regex either way

> 3. faster is: find . -name "*.wav"
this one is kosher, maybe with **-i**name for case insensitiveness

---

### Post by Impavidus on 2012-11-07
```
ls -ltR /home/k/Documents |grep -i '.wav'
```
will give you all files with wav (case insensitive) in them, exept those starting with wav (unless the string wav occurs twice). This is because grep doesn't use a simple string, but a regular expression and "." matches on any single character.

You could use
```
ls -ltR /home/k/Documents | grep -i '\.wav\>'
```
"\." matches on ".", "\>" matches on the end of a word, so this will match precisely on files with the .wav extension.

---

### Post by Kevin McCready on 2012-11-08
Thanks. You guys are awesome.

One more little problem. I'd love to list the full path for each file with ls.

Then I can highlight it in the results, use my middle mouse button and open it.

---

### Post by Vaphell on 2012-11-08
you have to use *find* then
```
find /home/k/Documents -iname '*.wav'
```
would print the list of full paths starting with that /home/k/Documents. Find returns results that start with the path provided
find . -> ./some_dir/some_file.wav
find /some/dir -> /some/dir/some_other_dir/some_file.wav

In case you want to scan . (current directory) but get full paths you can use *find "$PWD"* ... - PWD variable stores full path of current location

---

