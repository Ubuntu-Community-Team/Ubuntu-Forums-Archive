---
title: "Is there any Systems Dynamics software packaged for Ubuntu?"
date: 2013-09-07
forum: General Help
---

### Post by lads on 2013-09-07
I'm looking for [Systems Dynamics]("https://en.wikipedia.org/wiki/System_dynamics") software (e.g. [Stella]("http://www.iseesystems.com/softwares/Education/StellaSoftware.aspx")) for Ubuntu, preferably open source. Recommendations for non packaged software that runs on Linux are also welcome.

Thanks.

---

### Post by rai_shu2 on 2013-09-07
I think the [iModeler]("http://www.consideo.com/") is the only software like that which also runs in Linux.

---

### Post by lads on 2013-09-07
> **rai_shu2 said:**
> I think the [iModeler]("http://www.consideo.com/") is the only software like that which also runs in Linux.

Thank you for the suggestion, but I can't recognise any of the traditional System Dynamics concepts in that software.

---

### Post by rai_shu2 on 2013-09-07
Maybe something like [JMCAD]("http://jmcad.sourceforge.net/index_us.shtml")? I'm not sure exactly what you're looking for, to be honest.

---

### Post by lads on 2013-09-07
> **rai_shu2 said:**
> I'm not sure exactly what you're looking for, to be honest.

I'm looking for [System Dynamics]("https://en.wikipedia.org/wiki/System_dynamics") software.

---

### Post by rai_shu2 on 2013-09-07
Yeah, I read that and it left me scratching my head. Most computer programs have some kind of definite purpose, but what you're looking for is really very vague and hard to describe.

> System dynamics have various "back of the envelope" management applications. They are a potent tool to:

[LIST]
[*]Teach [system thinking]("https://en.wikipedia.org/wiki/System_thinking") reflexes to persons being coached
[*]Analyze and compare assumptions and [mental models]("https://en.wikipedia.org/wiki/Mental_models") about the way things work
[*]Gain qualitative insight into the workings of a system or the consequences of a decision
[*]Recognize archetypes of dysfunctional systems in everyday practice
[/LIST]

---

### Post by lads on 2013-09-08
> **rai_shu2 said:**
> but what you're looking for is really very vague and hard to describe.

Ignorance is a great thing. System Dynamics was one of the very first applications of computers, with the initial models developed in assembler language still in the 1950s. This eventually gave birth to [DYNAMO]("https://en.wikipedia.org/wiki/DYNAMO_%28programming_language%29"), the first computer simulation language.

If you did not know what System Dynamics is you could have just read the links I furnished.

---

### Post by rai_shu2 on 2013-09-08
Yeah, see. I've read all that stuff, and I'm still not sure what System Dynamics is. Is it for real, or honestly is it just some academics double-speak? It looks impressive. I'll give it that, but my mind won't let me BELIEVE that it actually means something. I read it, and I can't help but think that I'm reading the pitch of a brilliant con artist.

---

### Post by HiImTye on 2013-09-08
not sure if this is what you're looking for, as I also don't fully understand what it is.
[quote=https://help.ubuntu.com/community/UbuntuScience][Simile]("http://www.simulistics.com/") - A  proprietary ($$$) System Dynamics and object-based modeling and  simulation software package similar to Stella, Model Maker, Vensim, etc.  It is advertised as "Visual modeling software for the earth,  environmental and life sciences". A free evaluation version, which  limits the size of saved models, is available"[/quote]

---

### Post by lads on 2013-09-09
> **rai_shu2 said:**
> I can't help but think that I'm reading the pitch of a brilliant con artist.

Thank you for the compliment. And btw, don't bother wasting my time any longer.

---

### Post by lads on 2013-09-09
> **HiImTye said:**
> not sure if this is what you're looking for, as I also don't fully understand what it is.

Thanks that's a good suggestion. There doesn't seem to be a time limit on the evaluation version, which essentially makes it free software.

---

### Post by lads on 2013-09-11
The answer to this question appear to be no. These past few days I found several free or open source System Dynamics programmes that should run on Ubuntu, but none is packaged at this time; some of them are just code libraries. Here's the list:

  [LIST]
  [*][DynSim]("http://code.google.com/p/dynsim/wiki/Intro") - a Java package, apparently undocumented.

   [*][MapSim]("http://mapsim.sourceforge.net/") - a simulation engine for System Dynamics. Provides a .NET library that works on Windows and under Mono on Linux plus a simple GUI tool. MapSim uses its own modeling language described in a reference manual.

   [*][NetLogo]("http://modelingcommons.org/tags/one_tag/266") - the famous agent based modelling framework; supports system dynamics models as a secondary feature.

    [*][Sphinx SD Tools]("http://sourceforge.net/projects/sphinxes/") - a project dedicated to create common accessible environment for System Dynamics simulation. It is developed on the Java 6 platform and uses the Java Swing GUI.

    [*][SystemDynamics]("http://sourceforge.net/projects/system-dynamics/") - a graphical Java application for modelling, visualization and execution of System Dynamics models.

    [*][Simile]("http://www.simulistics.com/") - A proprietary System Dynamics and object-based modelling and simulation software package similar to Stella, Model Maker, Vensim, etc. A free evaluation version, which limits the size of saved models, is available.
[/LIST]

---

