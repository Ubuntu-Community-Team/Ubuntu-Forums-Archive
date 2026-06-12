---
title: "Problems running executables"
date: 2007-02-10
forum: General Help
---

### Post by lbyrd33 on 2007-02-10
Im an old Fedora user, but now I am running Edgy. I just realized on about two occasions now that I have not been able to run any executables that I have tried after installing certain software. For example when installing this sparky software, i changed into the installed directory and the ubuntu software shows the file their and that it is an executable. Following the commercial instructions I then run:

:/usr/local/sparky/bin$ ./sparky
bash: ./sparky: /bin/csh: bad interpreter: No such file or directory

The file is definately there:

/usr/local/sparky/bin$ ls
bruk2ucsf    peaks2ucsf  sparky            ucsfdata
matrix2ucsf  pipe2ucsf   sparky-no-python  vnmr2ucsf

Even running this command with the sudo permission resulted in the same product. I have had Sparky installed on my old FC 4 computer. Any help on this matter would be great. If anymore information is needed just let me know.

---

### Post by Shortgeek on 2007-02-10
It's not saying that ./sparky isn't there, I think it's saying that /bin/csh isn't there.

Also, what's in the ./sparky file?

---

### Post by lbyrd33 on 2007-02-10
The sparky file should start up the graphics for the program. Im a chemist and this is a tool for processing NMR data.

---

### Post by lbyrd33 on 2007-02-11
I just had to install the csh ubuntu package. Im surprised that this wasnt included in the base system of ubuntu.

---

