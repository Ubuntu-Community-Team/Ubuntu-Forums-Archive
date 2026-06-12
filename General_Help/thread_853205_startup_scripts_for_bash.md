---
title: "startup scripts for bash"
date: 2008-07-08
forum: General Help
---

### Post by soccersups on 2008-07-08
Hi. 
I recently switched to Ubuntu hardy heron and am trying to use MEXFILES in MATLAB. It requires me setting environment variables in the start up scripts. The mathworks website only gives directions for the cshell and the bourne shell, but hardy heron ( i think) is using the bash shell - at least when using matlab. Thus, putting the environment in .profile doesn't work because it is using the bash shell. (in matlab i get  :
>> !engdemo
/bin/bash: engdemo: command not found
)

Where are the startup scripts for the bash? Or am I thinking of this in the wrong way?

I suspect my lack of understanding of shell's is my issue. Any help please? 

Here is a link to what i'm trying to do:

[http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/matlab_external/f29148.html&http://www.google.com/search?hl=en&q=matlab+engine&btnG=Google+Search](http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/matlab_external/f29148.html&http://www.google.com/search?hl=en&q=matlab+engine&btnG=Google+Search).


Thanks.

---

### Post by joshsmith on 2008-07-08
tell us what you put in the .profile file

the site says you need csh, so do sudo apt-get install csh

also, if you didnt know, bash stands for bourne again shell, so is the borne shell

---

### Post by soccersups on 2008-07-08
Sorry, I posted the wrong link. 

[http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/matlab_external/f39903.html&http://www.mathworks.com/access/helpdesk/help/techdoc/helptoc.html](http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/matlab_external/f39903.html&http://www.mathworks.com/access/helpdesk/help/techdoc/helptoc.html)

What I put into .profile was:

LD_LIBRARY_PATH=matlabroot/bin/glnx86: matlabroot/sys/os/glnx86:$LD_LIBRARY_PATH

export LD_LIBRARY_PATH. 

The directions on the new link says I can do it in bourne shell... I already tried installing c shell, but couldn't find the .cshrc file. 



thanks for the help.

---

### Post by soyuz_one on 2008-07-13
I'm in the same situation, how did you solve the problem?

---

