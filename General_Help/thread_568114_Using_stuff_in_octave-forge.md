---
title: "Using stuff in octave-forge"
date: 2007-10-05
forum: General Help
---

### Post by LarsP on 2007-10-05
I have installed octave 2.9  and octave-forge. I want to use imread in octave-forge. How do i get octave to use .m-files in /usr/share/octave/site/api-v22/m/octave2.9-forge/image/ ?

---

### Post by jUser on 2007-10-30
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/bugs/157050](https://launchpad.net/bugs/157050) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm also looking for a solution to this. Something is probably wrong with the packages for version 2.9. Using octave2.1 and octave2.1-forge works just fine.

---

### Post by shoofy on 2007-11-21
If you want to get imread and other image functions working you can execute these commands in octave, but to get the rest of octave forge you'll have to do the same thing with the rest of the subdirectories:
> addpath('/usr/share/octave/site/api-v22/m/octave2.9-forge/image/')
savepath

---

### Post by Mlehliw on 2007-12-01
Is this really the only way to do this? There has to be a better way isn't there.

---

### Post by shoofy on 2007-12-01
There is. Use octave2.1. It's just less true to MATLAB syntax, which was a problem for me when I was working on a project jointly with people using MATLAB.

---

