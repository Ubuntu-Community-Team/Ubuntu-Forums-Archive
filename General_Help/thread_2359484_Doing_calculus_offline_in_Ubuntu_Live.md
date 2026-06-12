---
title: "Doing calculus offline in Ubuntu Live"
date: 2017-04-24
forum: General Help
---

### Post by haplorrhine on 2017-04-24
I want to do basic calculus calculations from an offline session of Ubuntu Live 16.04.  My calculator is quickly draining the batteries and my laptop has no harddrive, but it would be much easier to learn the calculus notation and the balancing of calculus equations if I had a calculator that could check that a function gives the expected outputs.  If I cannot do this from the command-line nor with "Calculator" or "LibreOffice Calc", then is there a bash script that I could quickly type up and execute?

---

### Post by TheFu on 2017-04-24
You can install a symbolic math package into a Live Ubuntu running system.  
[https://help.ubuntu.com/community/UbuntuMath](https://help.ubuntu.com/community/UbuntuMath) has a few options.  Back when I was doing calculus this way, I used MathCAD on Windows. Never tried to load it under WINE on Linux - need to check if my license will still work.

[https://ubuntuforums.org/showthread.php?t=1727273](https://ubuntuforums.org/showthread.php?t=1727273) has some other options that would be worth checking out. Many leads seem to be 3+ yrs ago. [https://sourceforge.net/projects/miramath/](https://sourceforge.net/projects/miramath/)

If real results, not symbolic, are needed, then there are many more options - octave. [http://wiki.octave.org/Octave_for_GNU/Linux](http://wiki.octave.org/Octave_for_GNU/Linux)

Used laptop drives can be had for $20, just visit your local mom-n-pop computer store and ask them. Then you could do an install.  Or you can get a USB flash drive with 32G of storage - think I saw one for $16 today.  Perform an install onto that storage.  A cheap SSD would be better and remove the flash memory overuse issue.

Just some options for your consideration.  Hope this is helpful.  Prefer to use packages from the Ubuntu Repos. If those aren't working for you, look for a PPA. Avoid .deb or source installs. 

Please post back what you decide to help the next people.

---

### Post by haplorrhine on 2017-04-25
I thought I knew enough shortcuts to obtain the derivative in most cases.  However, I might be okay even for the integrals.  In my case, learning basic electrical engineering, it may be enough to memorize the integral of sin(3.14x) from zero to one.  Sin(3.14x) has a period of 2, but I can just multiply this memorized value by (half of) the period of the function in question.  If that does not work out....

The integral is really what I need, and the approximation of definite integrals might be enough.  "Calculator" can handle trigonometric functions; if bash can too, then it should be easy to write a bash script that calculates an approximation for a definite integral.  The script might request three input strings: the function, range of integral, and interval between each successive value of x for f(x).  For inputs sin(x), 0.1-3.1, and 0.1; the script would take the average output of sin(x) where x is 0.1, 0.2, 0.3, ... 3.1.  This approximation might be close enough for someone who is only trying to learn.

---

### Post by TheFu on 2017-04-25
I was an ASE. Haven't used calculus directly in decades.  

Slopes and integrals are basic computer problems, easily solved. I wouldn't use bash, I'd use any real scripting language - most will have a Math library that supports differential and integral calculus work. Perl, Python, Ruby all will, I'm positive.  
* [http://rosettacode.org/wiki/Numerical_integration](http://rosettacode.org/wiki/Numerical_integration)
* [http://rosettacode.org/wiki/Euler_method](http://rosettacode.org/wiki/Euler_method)

Bash gets into some really ugly symbols when doing non-trivial math. Use python, if you are just starting out.  A basic computer programming class in python will teach both of those methods above.

---

### Post by monkeybrain20122 on 2017-04-25
As someone who teaches calculus the best way to learn is with pen and paper on which you can doodle freely. You don't need a calculator or any package. This is what I call abuse of technology. :)

---

### Post by LastDino on 2017-04-25
Alternatively you can use R to form a script for any set of fixed calculation process and run it on your data whenever you require. 

R is also free and slightly more inclined on data processing part than programing, but you can use it as your command like calculator too, for all the other operations like matrices and all...

---

### Post by monkeybrain20122 on 2017-04-25
> **haplorrhine said:**
> I thought I knew enough shortcuts to obtain the derivative in most cases.  However, I might be okay even for the integrals.  In my case, learning basic electrical engineering, it may be enough to memorize the integral of sin(3.14x) from zero to one.  Sin(3.14x) has a period of 2, but I can just multiply this memorized value by (half of) the period of the function in question.  If that does not work out....

The integral is really what I need, and the approximation of definite integrals might be enough.  "Calculator" can handle trigonometric functions; if bash can too, then it should be easy to write a bash script that calculates an approximation for a definite integral.  The script might request three input strings: the function, range of integral, and interval between each successive value of x for f(x).  For inputs sin(x), 0.1-3.1, and 0.1; the script would take the average output of sin(x) where x is 0.1, 0.2, 0.3, ... 3.1.  This approximation might be close enough for someone who is only trying to learn.

Sorry man your whole approach is wrong. First you don't have to "memorize" random integrals, that is not how to learn math. Secondly what you meant is sin(Pi*x) and Pi !==3.14, Pi is a irrational number and int(sin(pi*x), x, 0, 1) = (cos(0) - cos(pi))/pi = (1 - (-1)/pi = 2/pi because of the fundamental theorem of calculus. 

Pi is a very special and mysterious number, 3.14 on the other hand means squat. A bad habit that some people develop from high school is to abuse the calculator and convert all their answers to numerical approximations that are just gibberish which  don't reflect the structure of the solution. A good math teacher should tell you to keep all the pis and square root 2 etc in your answers.

---

### Post by monkeybrain20122 on 2017-04-25
> **LastDino said:**
> Alternatively you can use R to form a script for any set of fixed calculation process and run it on your data whenever you require. 

R is also free and slightly more inclined on data processing part than programing, but you can use it as your command like calculator too, for all the other operations like matrices and all...

As far as I know R is no good at symbolic calculations. Something like Maxima or Sage would be more appropriate. Anyway if OP's goal is to learn calculus rather than programming (unless he/she is doing numerical methods, but doesn't sound like it. In that case octave would be good) then it is better to do it with pen and paper than wasting time on fancy programming. Calculus is a very conceptual subject and a lot of it would make a lot more sense if one thinks in terms of geometry rather than numbers and formulas/

---

### Post by LastDino on 2017-04-25
> **monkeybrain20122 said:**
> As far as I know R is no good at symbolic calculations. Something like Maxima or Sage would be more appropriate. Anyway if OP's goal is to learn calculus rather than programming (unless he/she is doing numerical methods, but doesn't sound like it. In that case octave would be good) then it is better to do it with pen and paper than wasting time on fancy programming. Calculus is a very conceptual subject and a lot of it would make a lot more sense if one thinks in terms of geometry rather than numbers and formulas/

I haven't used Maxima or Saga, but I couldn't agree more on pen paper part and thinking rather than bi-hearting.

---

### Post by TheFu on 2017-04-25
> **monkeybrain20122 said:**
>  it is better to do it with pen and paper than wasting time on fancy programming. Calculus is a very conceptual subject and a lot of it would make a lot more sense if one thinks in terms of geometry rather than numbers and formulas/

+1 - in the beginning. 

For hundreds of years, people learned calculus without calculators. Computers and calculators often get in the way of real learning.

But as an engineer, you'll learn to never expect the exact answer provided by math to be more than a guide for what happens in the real world. There are always physical world losses and equation simplifications do not address all of them. Always.

---

### Post by QIII on 2017-04-25
Back in my University years (all 8 of them) it was purely stubby pencil and slide rule work.  The conceptual part was stubby pencil.  Used a slide rule to apply it.

Actually "Calculus" or "The Calculus" (depending on which Math historian attributes its modern codification to whom) was well known to the Greeks.  The just didn't have the symbolic language for it.

Although I used Calculus in bridge designs, a whole lot of decisions are based on real-world observations of what has and has not worked well for several thousand years...

---

