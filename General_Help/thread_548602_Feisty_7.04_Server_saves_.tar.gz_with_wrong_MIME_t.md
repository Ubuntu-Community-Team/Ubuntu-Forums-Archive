---
title: "Feisty 7.04 Server saves .tar.gz with wrong MIME type"
date: 2007-09-11
forum: General Help
---

### Post by kenlyle on 2007-09-11
I am trying to manage my Joomla sites from Edubuntu, but something in either Firefox or the OS is fouling me.

I download and save a file like that named in the error message below, and expect that .tar.gz will be recognized intelligently and correctly, but it's not.  Trying to open it, I get this error:

The filename "com_joomlaxplorer_1.6.1.tar.gz" indicates that this file is of type "tar archive (gzip-compressed)". The contents of the file indicate that the file is of type "plain text document".

I've waded through a lot of blather on the forums about this, but am really just looking for a solution.  For now, I am going to use Windows XP, for this type of operation, which is a step backward that I regret having to make.

Thanks,
K

---

### Post by Jasper84 on 2007-09-12
I am not sure, i do not really use nautilus much, but looking into it, right clicking on a file, clicking 'properties', then under the 'open with', you can add programs or commands that will open that type of file. I suggest you try opening it with the 'Archive Manager'.(I think it should defaultly be archive manager)  Make sure the little checkbox is lit?

Perhaps that is not the problem, you can also try 'tar -xf com_joomlaxplorer_1.6.1.tar.gz' from commandline.(in correct directory)

---

### Post by kenlyle on 2007-09-12
I am afraid that's not quite it.  Read the error message again.  

I tried Open With, and two different Archive Manager and XArchiver.  The first gives me an error, after which the icon changes from a .zip icon to a text file icon, and the second brings up an empty box.

In repeated attempts to download the file (to an NTFS formatted USB drive), the Save dialog represents that the file is of type .tar.gz archive, but the file comes down 0 bytes, of type text/plain.

I am going to have to use Windows for this for now.

K

---

