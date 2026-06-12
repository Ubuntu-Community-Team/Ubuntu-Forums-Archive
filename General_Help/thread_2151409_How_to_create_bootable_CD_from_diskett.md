---
title: "??  How to create bootable CD from diskett"
date: 2013-06-04
forum: General Help
---

### Post by Gobugs on 2013-06-04
Howdy

I am trying to create a bootable CD from a DOS bootable diskett,  using genisoimage so I can use existing apps on it.  I am missing something and would appreciate any help or suggestions.

On an Old PC with diskett.
Using ubuntu12 live cd, I copy the diskette
   sudo dd if=/dev/fd0 of=floppy.image   (this works as I dd it to a clean diskette and it booted and worked fine)

Moving the floppy.image to a Xubuntu12 PC  to  $H/temp
cd to temp

sudo genisoimage -o floppy.iso  floppy.image
baraso to burn to cd 
     (Nope!, this don't boot and I don't see the files and executables)

Trying  again telling genisoimage it is a diskette image

sudo genisimage -o floppy.iso -r -b floppy.image 
   (Nope!   genisoimage fails with an erorr 
          genisoimage: Missing pathspec. 
          Usage: genisoimage [options] -o file directory ...

Surely that can't be for the output as it is ok in the first try  ??  Right  ??
And because I'm using floppy.image within the same directory,  that should be ok ?? Right ??

What am I missing?
Thanks.

---

### Post by 25tom on 2013-06-04
Maybe you should put the ' -r -b' before the ' -o'? It seems that genisoimage is taking '-r -b' as the source path. You should, as a general rule, put options before arguments, that is to say, '-whatever' (usually a hyphen then single letter) options all come before the 'arguments', files/whatever that the command is going to use/modify etc...

So you'd put```
[COLOR=#000000]sudo genisoimage -o -r -b floppy.iso floppy.image[/COLOR]
```

Hope this helps :)

---

### Post by Gobugs on 2013-06-04
Ok,    I  tried your suggestion and YES it did remove  "that" error,   but it generated another  


sudo genisoimage -r -b -o floppy.iso floppy.image

genisoimage: No such file or directory. Invalid node - 'floppy.iso

I also tried the sequence of  -o -r -b  ....    and got the same results.
I read the man page as the -o option defines the output file which is to be in iso format.

I searched for a genisoimage forum,,, but none popped up.
Any other suggestions or different methods of achieving the same end results ??

Thanks.

---

