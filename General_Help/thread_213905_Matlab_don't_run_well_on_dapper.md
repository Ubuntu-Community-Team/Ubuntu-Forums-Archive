---
title: "Matlab don't run well on dapper"
date: 2006-07-11
forum: General Help
---

### Post by 3str on 2006-07-11
I have a Matlab 7.04(SP2) which worked nicely under breezy. When I installed on a dapper system, the Open File dialog doesn't work well. If I double click the directory list on the left, the current directory won't change. If I double click the file list on the right, it says the file doesn't exist.

Would anyone help? Thx!

---

### Post by slimdog360 on 2006-07-12
This is probably more of a question which you should direct at matlab themselves because I dont think to many people here use it in linux.

---

### Post by buttari on 2006-07-12
Tha Matlab GUI is extremely unstable in linux. I tried it on gentoo, breezy and dapper and it was always crashing very often. My suggestion is to use Matlab without the GUI:

```
$ matlab -nojvm
```

regards,
alfredo

---

### Post by leeyee on 2006-07-12
I think so, Matlab's GUI is always unstable. I'm using Scilab now!

---

### Post by buttari on 2006-07-12
Is Scilab compatible with Matlab? I mean: if I take a Matlab source, will it run on Scilab?

alfredo

---

### Post by neutro on 2006-07-12
> **3str said:**
> I have a Matlab 7.04(SP2) which worked nicely under breezy. When I installed on a dapper system, the Open File dialog doesn't work well. If I double click the directory list on the left, the current directory won't change. If I double click the file list on the right, it says the file doesn't exist.


Using Matlab 7.2 (R2006a), I can sort of reproduce your problem. Try this: double-click really fast. For some reason, the Matlab UI has its own click-repeat rate, and is set way too high. Well, this seems to work for me, anyway.

As for Matlab compatibility: Octave is probably the most Matlab-compatible interpreter here (but there's no GUI for Octave, so you're even better with matlab -nojvm). Octave supports a subset of the Matlab language (corresponding, approximately, to what Matlab was at v.4 or so), plus some Octave-specific constructs.

---

### Post by Najand on 2006-07-12
> **3str said:**
> I have a Matlab 7.04(SP2) which worked nicely under breezy. When I installed on a dapper system, the Open File dialog doesn't work well. If I double click the directory list on the left, the current directory won't change. If I double click the file list on the right, it says the file doesn't exist.

Would anyone help? Thx!


I don't know how to fix your problem, but I was using Matlab at breezy and still using it on Dapper with both i386 and ppc architectures without any problem. Even yesterday, after upgrading to a newer Kernel I used the GUI version of Matlab to write and run a program. 
Maybe some packages you were not using in Breezy and are now using it in Dapper (Not neccessorily related to Matlab) like SCIM or somethiing  else is in conflict with Matlab. It was not Matlab, but I had problem with RealPlayer after upgrading to Dapper because it was in conflict with scim, which the upgrade process replaced uim I used to use without ant notice.

---

### Post by leeyee on 2006-07-12
Really? Maybe I should re-install Matlab on Dapper.....

---

### Post by krazyd on 2006-07-13
I hate to say it guys, but it's much, much easier just to dual boot for matlab.. IMHO ;)

---

### Post by neutro on 2006-07-13
> **krazyd said:**
> I hate to say it guys, but it's much, much easier just to dual boot for matlab.. IMHO ;)

While I concur that the Matlab GUI in v.7+ for Linux is still far from optimal (hey, I'd really love to be able to type that carret ^ into the command window or editor using my everyday keyboard layout!), it's still *much* better than what it was in Matlab 6 and 6.5.

Also, Matlab 64-bits on Linux 64-bits blows everything else for many tasks.

I for one simply use two computers at job, one booted in Windows and the other in Ubuntu :P 

(Oh yeah, and ugh, isn't installing Matlab a hassle in Linux compared to Windows... I guess the only way to see a better Linux Matlab is to tell TheMathWorks that you use Matlab in Linux, and that you CARE about it.)

---

### Post by tkjacobsen on 2006-07-13
> **buttari said:**
> Is Scilab compatible with Matlab? I mean: if I take a Matlab source, will it run on Scilab?

alfredo

Scilab and matlab dont use the same syntax. Try octave instead (you'll need octave-forge - both in universe). Octave (allmost) uses the same syntax as matlab. My last matlab project ran flawlessly in octave including plots (for this you also need gnuplot). See [http://octave.sourceforge.net/](http://octave.sourceforge.net/) for more details and documentation, there even is a matlab to octave conversion guide somwhere.

Octave <-> Matlab Compatibility Database
[http://users.powernet.co.uk/kienzle/octave/matcompat/](http://users.powernet.co.uk/kienzle/octave/matcompat/)

---

### Post by 3str on 2006-07-14
Well, I posted my question on Mathworks site. I was told to type the filename and enter instead of click in the list. It worked, though seems a little stupid:-)

---

### Post by slimdog360 on 2006-07-14
Ive asked this question about 100 times but no one will give me an answer so Im trying it in here. 
When I compile Scilab from source it comes up with the error X Window not found. I dont know how to fix that so if someone could give me anything, even just what it means so I can try to solve it myself.
Ive also tried installing it with synaptic but the language is set in Hindi (I think) and I cant read Hindi so its no good. Can anyone tell me how to change the language???
thanks

---

### Post by J77 on 2006-10-25
Matlab with or without the gui work fine for me on Breezy - including running 4 memory intensive sessions at the same time (ie. on all 4 processors).

Major problems on 6.06LTS - see my most recent posts :(

---

### Post by iSYS on 2007-11-07
I have the *same* problem (and I tried clicking very quickly, to no avail) - has anyone been able to fix this little irksome beast?

---

