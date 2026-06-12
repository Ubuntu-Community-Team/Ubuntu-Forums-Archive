---
title: "Terminal rename and move - [not what you think]"
date: 2012-11-04
forum: General Help
---

### Post by ntzrmtthihu777 on 2012-11-04
Greetings,

Ok, I bet you are thinking "this has been asked and answered, search the forums before you post n00b" but this is a unique situation with (I hope) a unique solution. 

Some background: I used the terminal to download a large amount of .jpg files from [www.wizards.com]("http://www.wizards.com") (available for private use) and ended up with (by design) files with names like this:

leaving.asp?url=%2Fdnd%2Fimages%2Fpsi_gallery%2FPsi_1.jpg
leaving.asp?url=%2Fdnd%2Fimages%2Fpsi_gallery%2FPsi_2.jpg
leaving.asp?url=%2Fdnd%2Fimages%2Fpsi_gallery%2FPsi_3.jpg
...and so on.

what I want to know, is it possible to rename these files en masse, and move them based on the resulting name, say:

leaving.asp?url=%2Fdnd%2Fimages%2Fpsi_gallery%2FPsi_1.jpg
leaving.asp?url=%2Fdnd%2Fimages%2Fpsi_gallery%2FPsi_2.jpg
leaving.asp?url=%2Fdnd%2Fimages%2Fpsi_gallery%2FPsi_3.jpg

into

/home/username/dnd/images/psi_gallery/Psi_1.jpg
/home/username/dnd/images/psi_gallery/Psi_2.jpg
/home/username/dnd/images/psi_gallery/Psi_3.jpg

Preferably in some manner that replaces "leaving.asp?url=" with "/home/username" and the remaining "%2F" with "/"

I have already attempted this with Gprename, and as useful as that is it does not do the trick here. If it is not possible I can make do with what I know, but I should really like to have this done properly and organized. Assume the directories are already made.

Any tips, tricks, and how-tos would be appreciated!

---

### Post by steeldriver on 2012-11-04
Well it looks like the perl-based 'rename' command will do multiple substitutions in one go separated by ';' (like sed) i.e.

```
rename -nv 's#leaving\.asp\?url=#/home/username#;s#%2F#/#g' *.jpg
```(the target directory must already exist) - if it looks like it's doing the right thing then remove the 'n' switch to do it for real

---

### Post by ntzrmtthihu777 on 2012-11-04
Well I dun goofed, lol. I ran the code as-is, and forgot to substitute my own username, lol. Posting this here as an example of what NOT to do, lol.

```
rename -nv 's#leaving\.asp\?url=#/home/username#;s#%2F#/#g' *.jpg
leaving.asp?url=%2Fdnd%2Fimages%2Fpsi_gallery%2FPsi_25.jpg renamed as /home/username/dnd/images/psi_gallery/Psi_25.jpg
```

```
rename -v 's#leaving\.asp\?url=#/home/username#;s#%2F#/#g' *.jpg
Can't rename leaving.asp?url=%2Fdnd%2Fimages%2Fpsi_gallery%2FPsi_25.jpg /home/username/dnd/images/psi_gallery/Psi_25.jpg: No such file or directory
```

---

### Post by dino99 on 2012-11-04
nautilus-filename-repairer should do the job.

otherwise here is an other way:
[https://code.google.com/p/nautilus-batch-rename/downloads/list](https://code.google.com/p/nautilus-batch-rename/downloads/list)

---

### Post by ntzrmtthihu777 on 2012-11-04
> **steeldriver said:**
> Well it looks like the perl-based 'rename' command will do multiple substitutions in one go separated by ';' (like sed) i.e.

```
rename -nv 's#leaving\.asp\?url=#/home/username#;s#%2F#/#g' *.jpg
```(the target directory must already exist) - if it looks like it's doing the right thing then remove the 'n' switch to do it for real
Hmm, here is another question, is there a way to "pipe in" the results of

```
cut -d\" -f10 page.html | grep 'default.asp?x=dnd/pc/' |
sort -u | while read link;do echo "http://www.wizards.com$link";done |
while read page; do lynx --dump "$page" | grep "url=/dnd/" |
awk '{print $2}';done | cut -d\& -f1 | while read img;do wget -c "$img";done
```(the code by which I got the images) into

```
rename -nv 's#leaving\.asp\?url=#/home/username#;s#%2F#/#g' *.jpg
```so that they are automatically renamed as you save them? I tried the good old | in between, but that is not cutting it here. Don't get me wrong, downloading them first and then renaming them works just fine, I just would like to be able to do it at one go in this script I am writing.

---

### Post by Nutria on 2012-11-04
> **ntzrmtthihu777 said:**
> Greetings,

Ok, I bet you are thinking "this has been asked and answered, search the forums before you post n00b" but this is a unique situation with (I hope) a unique solution. 

Some background: I used the terminal to download a large amount of .jpg files from [www.wizards.com]("http://www.wizards.com") (available for private use) and ended up with (by design) files with names like this:

leaving.asp?url=%2Fdnd%2Fimages%2Fpsi_gallery%2FPsi_1.jpg
leaving.asp?url=%2Fdnd%2Fimages%2Fpsi_gallery%2FPsi_2.jpg
leaving.asp?url=%2Fdnd%2Fimages%2Fpsi_gallery%2FPsi_3.jpg
...and so on.

what I want to know, is it possible to rename these files en masse, and move them based on the resulting name, say:

leaving.asp?url=%2Fdnd%2Fimages%2Fpsi_gallery%2FPsi_1.jpg
leaving.asp?url=%2Fdnd%2Fimages%2Fpsi_gallery%2FPsi_2.jpg
leaving.asp?url=%2Fdnd%2Fimages%2Fpsi_gallery%2FPsi_3.jpg

into

/home/username/dnd/images/psi_gallery/Psi_1.jpg
/home/username/dnd/images/psi_gallery/Psi_2.jpg
/home/username/dnd/images/psi_gallery/Psi_3.jpg
[snip]
Any tips, tricks, and how-tos would be appreciated!

Haven't tested this, but if psi_gallery is under the current dir, and the images are in the current dir, this should work:

```
$ for f in leaving.asp*jpg; do n=$(echo "$f" | cut -c49-); mv -v "$f" psi_gallery/"$n"; done

```

---

### Post by steeldriver on 2012-11-04
> **ntzrmtthihu777 said:**
> Hmm, here is another question, is there a way to "pipe in" the results of [...] (the code by which I got the images) into

```
rename -nv 's#leaving\.asp\?url=#/home/username#;s#%2F#/#g' *.jpg
```so that they are automatically renamed as you save them?

I'm not much of a wget expert but I think you should be able to do that on the fly using the -O flag to specify a name for the local file, something like

```
wget -O "$img_local" -c "$img"
```where you can derive img_local from img using essentially the same regex substitution - either using sed e.g.

```
$ img="leaving.asp?url=%2Fdnd%2Fimages%2Fpsi_gallery%2FPs i_2.jpg"
$ img_local=$(echo "$img" | sed 's#leaving\.asp?url=#/home/username#;s#%2F#/#g'); echo "$img_local"
/home/username/dnd/images/psi_gallery/Ps i_2.jpg
```or using the bash ${parameter//pattern/substitution} syntax, e.g.

```
$ img_local=${img//leaving\.asp\?url=/"/home/username"}; img_local=${img_local//%2F//}; echo "$img_local"
/home/username/dnd/images/psi_gallery/Ps i_2.jpg
```(unfortunately I don't think there's any way to do both substitutions in one go with the bash syntax)

---

### Post by Vaphell on 2012-11-04
additionally /home/username can be replaced by $HOME which is maintenance free ;-)

```
$ f="leaving.asp?url=%2Fdnd%2Fimages%2Fpsi_gallery%2FPsi_1.jpg"
$ fl=${f/#*=/$HOME}; fl={fl//%2F//}
$ echo "$fl"
/home/me/dnd/images/psi_gallery/Psi_1.jpg
```

---

### Post by ntzrmtthihu777 on 2012-11-04
Ah, thank you all so very much, have gotten what I needed done. I have one more query, and I shall be set: I have managed to use the command line to list all the .jpg files, but cannot get them into a .txt file for error checking I am using:
```
cat list1.txt | grep "http://www.wizards" | while read page;
do lynx -source "$page" | grep "url=/dnd/images/" | cut -d\& -f1 | sort -u;done
```but I need to pipe the output into a text file, say list2.txt. Any of you ubuntu wizards got something for this?

---

### Post by Vaphell on 2012-11-04
> ```
[COLOR="Blue"]cat list1.txt | grep "http://www.wizards" |[/COLOR] while read page;
do lynx -source "$page" | grep "url=/dnd/images/" | cut -d\& -f1 | sort -u;done
```

you get better readability when you construct while read loop like this:

```
while read page
do
  lynx -source "$page" | grep "url=/dnd/images/" | cut -d\& -f1 | sort -u
done [COLOR="Blue"]< <( grep "http://www.wizards" list1.txt )[/COLOR] > list2.txt
```

also *grep* can work with files just fine so there's no need to have that unnecessary *cat* step 
> list2.txt at the end will dump the whole output of while read scope to the file.

---

