---
title: "Terminal, help needed"
date: 2015-04-30
forum: General Help
---

### Post by laszlo-halasz on 2015-04-30
Hi guys! First time poster here!

I have a small, but head scratching problem. Forgive me, I am a bit noob in this so be gentle :)

I have a program that creates a file which begins with a random date and I have to rename this file using a script.
To be precise, I will give you the exact part of the script.

This is of course not working:

mv $BASE_DIR/DICOM/DIFFUSION/20*.bvec $BASE_DIR/DICOM/DIFFUSION/bvec

The output is bevy without an extension.

How to change the above line?

Thank you in advance.

---

### Post by coffeecat on 2015-04-30
Support, not chat.

*Thread moved to **General Help**.*

---

### Post by Lars Noodén on 2015-04-30
> **laszlo-halasz said:**
> 
I have a program that creates a file which begins with a random date and I have to rename this file using a script.

You would use the utility 'rename' for that, but can you give a few examples of real file names and what you want them transformed to?

---

### Post by laszlo-halasz on 2015-04-30
Hi!

I have to this with mv to be universal, as another research center also would like to use my script.

Here is an exact file name:

20[COLOR=#ff0000]130901_091834DBSKUTATAS8s005a1001[/COLOR].bvec 

The red part is totally random. Its contents and length are always different. It has to be renamed to "bvecs", without an extension. It is a text file containing some information about the MRI acquisition.

---

### Post by Lars Noodén on 2015-04-30
If it just one source file and the new name is to only be "bvecs" then you should be able to do it using 'mv' as you have above.  

```

mv $BASE_DIR/DICOM/DIFFUSION/20*.bvec $BASE_DIR/DICOM/DIFFUSION/bvecs

```

I was thinking if you had many files and wanted to change the part after the underscore or the extensions for them you would use 'rename'.  But for one file 'mv' works.

---

### Post by laszlo-halasz on 2015-04-30
This won't, no such file or directory. Does it think that bvecs is a directory and fails?

---

### Post by Lars Noodén on 2015-04-30
Is the variable $BASE_DIR set to a useful value?
You could put an echo in your script to verify what you are actually moving:

```

echo mv $BASE_DIR/DICOM/DIFFUSION/20*.bvec $BASE_DIR/DICOM/DIFFUSION/bvecs
mv $BASE_DIR/DICOM/DIFFUSION/20*.bvec $BASE_DIR/DICOM/DIFFUSION/bvecs

```

---

### Post by laszlo-halasz on 2015-04-30
[FONT=Menlo]BASE_DIR=[COLOR=#d12f1b]`pwd` and it is working everywhere else[/COLOR][/FONT]

---

### Post by Lars Noodén on 2015-04-30
Does the subdirectory ./DICOM/DIFFUSION/ exist inside $BASE_DIR?

---

### Post by laszlo-halasz on 2015-04-30
The script is within the patient's folder. In this case

/Patients/DoGu/DICOM/DIFFUSION/

The script is initiated within the patients folder, in this case /Patients/DoGu/ , thus BASE_DIR is /Patients/DoGu/ in this case.

---

### Post by laszlo-halasz on 2015-04-30
Found out! :)

[FONT=Menlo]mv $BASE_DIR/DICOM/DIFFUSION/[COLOR=#272ad8]20[/COLOR]*.bvec $BASE_DIR/DICOM/DIFFUSION/bvecs.bvec[/FONT]
[FONT=Menlo][COLOR=#bb2ca2]for[/COLOR] i [COLOR=#bb2ca2]in[/COLOR] $BASE_DIR/DICOM/DIFFUSION/*.bvec; [COLOR=#bb2ca2]do[/COLOR] NEWNAME=[COLOR=#d12f1b]`echo "$i" | sed 's/\.bvec//'`[/COLOR]; mv [COLOR=#d12f1b]"$i"[/COLOR] [COLOR=#d12f1b]"$NEWNAME"[/COLOR]; [COLOR=#bb2ca2]done[/COLOR][/FONT]

---

### Post by Vaphell on 2015-04-30
wait a minute. Are you changing the *20*.bvec* name to *bvecs.bvec *and then stripping the extension to plain *bvecs* in a loop for a single item? o.O
btw, you don't need sed to strip the extension, *newname=${i%.*}* will do.

---

### Post by TheFu on 2015-05-01
> **Vaphell said:**
> 
btw, you don't need sed to strip the extension, *newname=${i%.*}* will do.

And since it is built-in, it will be 20x faster, more efficient. ;) Nice.

---

