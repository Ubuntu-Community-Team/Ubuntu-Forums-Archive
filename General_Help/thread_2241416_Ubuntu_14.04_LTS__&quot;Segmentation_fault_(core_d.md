---
title: "Ubuntu 14.04 LTS  &quot;Segmentation fault (core dumped)&quot; with two different softwares"
date: 2014-08-26
forum: General Help
---

### Post by joao_paulo5 on 2014-08-26
Made fresh isntallataion of the 14.04 LTS ubuntu in three different machines, all of them with the amd64 version. And all of them both GROMACS and pymol crash with the "Segmentation fault (core dumped)" error. I think its on the libc6 library (both o them use that library), but thats just a guess im lost on how i should proceed.

GROMACS will fail when i try to run any molecular dynamics job, and pymol will fail when i try to measure the distance between 2 atoms. To try to recreate the pymol error you can:

>sudo apt-get install pymol
>pymol

download any molecule structer (for example [http://www-jmg.ch.cam.ac.uk/data/molecules/misc/methane.pdb](http://www-jmg.ch.cam.ac.uk/data/molecules/misc/methane.pdb) )

go to pymol>file>open>methane.pdb , then pymol>wizard>measurement . Then proceed to click on 2 different atoms.

the program crashes and i get only :

Segmentation fault (core dumped).

I tested GROMACS with a fresh 14.04 LTS installation in 3 different machines and it failed. Then on the same computer i Installed  the 12.04 LTS version, and i didn't get any errors.

One way i found to "fix" the GROMACS problem on 14.04LTS was to manually install GROMACS following this guide [http://www.gromacs.org/Documentation/Installation_Instructions_4.6](http://www.gromacs.org/Documentation/Installation_Instructions_4.6) (and not via apt-get).

I've got 8 different computers to manage and manually installing different programs that should work via the repository doesn't seem right. At the moment the only thing im doing is to update daily the ubuntu and test the pymol measurement (not reinstalling it tho) to check if its still broken

Thank you!

---

### Post by dragonfly41 on 2014-08-26
I have absolutely nil experience in using GROMACS or pymol .. but given that this error occurs with two different programs
it may be that simply you are missing some Python or c libraries (dependencies).

e.g. for pymol do you need to install (search python-pmw in Ubuntu Software Centre)

python-pmw
python-tk
python-imaging

and for GROMACS do you need to install FFT libraries (search fftw in Ubuntu Software Centre)

libfftw3-3

...

Check the library dependencies for both GROMACS and pymol.

...

More here on debugging segmentation faults.

[http://jodal.no/post/5779178001/log-from-the-debugging-of-a-segfault/](http://jodal.no/post/5779178001/log-from-the-debugging-of-a-segfault/)

see also this tip in this thread ... post #2

[http://ubuntuforums.org/showthread.php?t=2233835](http://ubuntuforums.org/showthread.php?t=2233835)

which requires a temporary edit of /usr/share/pyshared/gobject/constants.py

to get around the segmentation error and find the root source of the problem.

But after debugging the seg fault you must reset constants.py to its original content.

...

The clue that your program runs on 12.04 but not 14.04 suggests some libraries are missing.

I hope that this helps since I'm guessing.

---

