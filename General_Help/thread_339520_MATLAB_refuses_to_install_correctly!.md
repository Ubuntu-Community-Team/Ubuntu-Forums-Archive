---
title: "MATLAB refuses to install correctly!"
date: 2007-01-15
forum: General Help
---

### Post by rayt5 on 2007-01-15
Hello. I am a long time forum user, first time poster. I have not had any major problems with Ubuntu or Linux in general, especially with installing software, until now.

After much hassle involving copying the CD to my hard drive, I was finally able to install Matlab & Simulink Student Version (release 14, service pack 3) on edgy.  However, when I try to run it, nothing happens. When I type matlab in the terminal, I get this error message:

**/home/ray/share/linux/Matlab71_sv/bin/glnx86/MATLAB: error while loading shared libraries: libicudata.so.32: cannot open shared object file: No such file or directory**

I went and found the libicudata.so.32 file it was talking about... it does exist. And I already changed the permissions of the file, so I know that's not the problem, either. ](*,) 

If anybody can help me get MATLAB working, their help would be greatly appreciated.  It's really a hassle to have to reboot into Windows just to use MATLAB, especially since I know this software is supposed to work for Linux in the first place...

---

### Post by rayt5 on 2007-02-14
bump

---

### Post by taurus on 2007-02-14
Where is libicudata.so.32 located anyway?  Make sure it's in your library path so matlab can find or else you would get that error message.

---

### Post by Adramelech on 2007-02-14
This can be a solution.

Add some_directory to your library path so that MATLAB will find it first:


setenv LD_LIBRARY_PATH /usr/some_directory: $LD_LIBRARY_PATH

---

### Post by rayt5 on 2007-02-15
I  just figured it out... the comment about the file being in the library helped me... I tried to install MATLAB all in my shared partition trying to save space instead of in the usual spot... I'm sure during the first installation attempt I told MATLAB to look somewhere wonky for the library. I reinstalled it in my /home/ray/ folder, and now it works perfectly. :)

---

### Post by meng on 2007-02-15
Ah congratulations on working it out. Erm, 4 weeks is a LONG time to wait to bump your thread, you must be very patient, there are folks here who'll bump their thread after 4 MINUTES.

---

