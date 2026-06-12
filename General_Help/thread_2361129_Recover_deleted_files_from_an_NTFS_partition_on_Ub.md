---
title: "Recover deleted files from an NTFS partition on Ubuntu Live USB"
date: 2017-05-12
forum: General Help
---

### Post by jakerh03 on 2017-05-12
Pretty specific problem here:

My friend's User folder in Windows got completely deleted. Their computer is suffering from some technical difficulties and fails to boot into Windows (perpetually in "Automatic Recovery," has already tried a reset).

I am running Ubuntu on a Live USB on their computer, and I need to find a way to undelete files from the NTFS Windows partition so I can get all of his documents and stuff back before I completely reset Windows.

How can I run an undelete-er on Ubuntu that will recover deleted files (**not the entire** **NTFS filesystem!!!**) so I can get his files back?

Thanksabunch
jakerh03

---

### Post by oldos2er on 2017-05-12
Give testdisk or photorec a try: [https://www.cgsecurity.org/](https://www.cgsecurity.org/)

If I were you I'd image the partition first (with something like clonezilla) and work from there if possible.

---

### Post by jakerh03 on 2017-05-12
Does photorec/testdisk recover docx files?

---

### Post by oldos2er on 2017-05-13
I don't know why it wouldn't. There is more info about it at the link I posted.

---

### Post by howefield on 2017-05-13
> **jakerh03 said:**
> Does photorec/testdisk recover docx files?

Yes it will.

Can't remember exactly where in the process to set it, but try setting the recovery to specific file formats, eg .docx otherwise you may end up with many thousands of files which will be mostly redundant and need sorting through.

---

### Post by dragonfly41 on 2017-05-13
When I last used Windows I found that Windows recovery apps were sometimes better in recovering Windows files.

Here is one I used in Vista.

[http://www.recovermyfiles.com/](http://www.recovermyfiles.com/)

You can experiment with a free trial to see if you can recover but the catch is you then have to pay for a licence.

Note that testdisk and photorec can also run in Windows.  
Just make sure that you have some external storage or partition at hand to save any recovered files.

[Edit]

i should add that in this scenario where the original Windows is not working/booting up
then the suggested Windows file recovery tools will need to be installed
in a separate working Windows environment and the target Windows hard drive 
physically removed and placed into a USB drive container
to be worked on.  At least that is what I had to do.

---

