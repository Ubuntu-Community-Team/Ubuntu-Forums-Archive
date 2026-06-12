---
title: "Cant start Dynare (from the repos)"
date: 2013-03-13
forum: General Help
---

### Post by Falc7 on 2013-03-13
So I'm trying to run a program called Dynare from the repositories. Heres a wiki link: [http://www.dynare.org/DynareWiki/InstallOnDebianOrUbuntu](http://www.dynare.org/DynareWiki/InstallOnDebianOrUbuntu)

I installed it, I start the program called octave, and that opens the terminal.

```
GNU Octave, version 3.6.2
Copyright (C) 2012 John W. Eaton and others.
This is free software; see the source code for copying conditions.
There is ABSOLUTELY NO WARRANTY; not even for MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  For details, type `warranty'.

Octave was configured for "x86_64-pc-linux-gnu".

Additional information about Octave is available at http://www.octave.org.

Please contribute if you find this software useful.
For more information, visit http://www.octave.org/help-wanted.html

Read http://www.octave.org/bugs.html to learn how to submit bug reports.

For information about changes from previous versions, type `news'.

warning: function /usr/share/octave/packages/statistics-1.1.3/fstat.m shadows a core library function
octave:1> dynare filename.mod
 
Configuring Dynare ...
[mex] Generalized QZ.
[mex] Sylvester equation solution.
[mex] Kronecker products.
[mex] Sparse kronecker products.
[mex] Local state space iteration (second order).
[mex] Bytecode evaluation.
[mex] k-order perturbation solver.
[mex] k-order solution simulation.
[mex] Quasi Monte-Carlo sequence (Sobol).
 
error: DYNARE: can't open filename.mod
error: called from:
error:   /usr/share/octave/site/m/dynare.m at line 104, column 5
octave:1> 

```

---

### Post by Falc7 on 2013-03-13
I've founded I needed to cd to the file where the .mod file was first. There doesn't seem to be an option to mark this thread solved

---

### Post by stinkeye on 2013-03-13
> **Falc7 said:**
> I've founded I needed to cd to the file where the .mod file was first. There doesn't seem to be an option to mark this thread solved

[**_[COLOR="#B22222"]How to mark threads SOLVED[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730")

---

