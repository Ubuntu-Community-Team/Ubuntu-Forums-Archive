---
title: "The library required for .7z"
date: 2007-09-30
forum: General Help
---

### Post by Kem Rixen on 2007-09-30
The thread title really says it all, I searched the forums and the wiki, but didn't come up with anything. So, do any of you happen to know the library required for 7Zip?

Also, I'm not entirely sure that this is the correct forum to be posting this in :oops:

---

### Post by Arwen on 2007-09-30
I have unrar and unace installed and I can zip-unzip .7z files..

---

### Post by diskotek on 2008-03-02
i can not manage it with "fileroller", it says "no support for this archive type". but as i see in description of file roller "it's supporting 7z". i searched on synaptic, and couldn't find any reliable solution for file roller + 7z.

---

### Post by julian67 on 2008-03-02
> **diskotek said:**
> i can not manage it with "fileroller", it says "no support for this archive type". but as i see in description of file roller "it's supporting 7z". i searched on synaptic, and couldn't find any reliable solution for file roller + 7z.

you can install p7ip-full from the repos. Fileroller and Xarchiver don't support all the features of 7z like unpacking encrypted archives or password protected archives but you can easily do it in the terminal, or if you prefer a gui try [PeaZip](http://peazip.sourceforge.net/) > PeaZip free archiver utility is a portable, open source archiving, encryption and file split tool.
PeaZip is cross platform and runs on 32 and 64 bit Windows (9x, 2000, XP, Vista) and Linux. It supports handling many archive and compression formats:

    *
      create: 7Z, ARC, BZ2, GZ, PAQ/LPAQ, PEA, QUAD, TAR, UPX, ZIP;
    *
      open: ACE, ARJ, CAB, DEB, ISO, LHA, RAR, RPM and more archive types...

PeaZip allows to edit, save and restore archive's layouts; apply powerful multiple filters to archive's content; handle multiple archives at once; export job definition as command line; encrypt with AES256 etc.
Other features: split/join files (file span), wipe files (secure deletion), compare, checksum and hash files, system benchmark, generate random passwords and keyfiles. I found it works really well in Ubuntu.

edit: correction: you still need to extract password protected 7z archives in the terminal. It's easy ```
7z e myarchive.7z
``` and it prompts for a password and then extracts.

---

