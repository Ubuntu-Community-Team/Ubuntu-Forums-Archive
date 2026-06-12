---
title: "Remote X applications failing due to fonts problems"
date: 2012-11-09
forum: General Help
---

### Post by denizs on 2012-11-09
Since I have upgraded from 10.04 to 12.04  I have not been able to run a variety of remote X-applications satisfactorily.   
 The problems may be due to not having the correct Xfonts installed but I am not sure
how to go about doing that.  Downloading font managers etc. did not help.
  For example SGE ( Sun Grid Engine ) QMON  fails to start 
and ANSYS selects a font that looks like Chinese writing. 

 Has anyone else had any similar problems and managed to get round them ? :(

---

### Post by denizs on 2012-11-09
I have resolved these problems by copying X11 fonts from a working installation
into my Ubuntu workstation under the directory ; 
        <home_directory>.fonts/fonts    

  It looks line the  fonts.cfg file  in /etc/fonts  is pointing to a wrong directory

  as the <dir> entry reads;      <dir>/usr/X11R6/lib/X11/fonts</dir>   

but the X11 software is not installed under  /usr/X11R6 .

---

### Post by rosswin on 2012-11-24
Hi

I am quite new to using Linux. I have Ubuntu 12.04.
I am connecting to a cluster at my university via "ssh -X". When I load Ansys I get the same issue as this. I have tried installing xfs.
I unfortunately don't have a working version of Linux on another computer where I can copy X11 across. I however found an X11 font folder in my computer directory and followed your instructions on where to put it.
After doing this I still get the same issue.

Is there a way for me to download the X11 folder and then paste it in a certain location or is there another way around my problem?

Thank you for your time.
Sorry if I am following the instructions incorrectly or if I haven't given enough information.

Regards,
Ross

---

