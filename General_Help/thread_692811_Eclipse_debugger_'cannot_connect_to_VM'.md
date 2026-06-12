---
title: "Eclipse debugger 'cannot connect to VM'"
date: 2008-02-10
forum: General Help
---

### Post by mr tim esquire on 2008-02-10
Hi, im trying to use eclipse to help me devolp java.
When i run the debugger i get an error message 
```
"cannot connect to VM" 
```
I have installed sun-java6-jdk so i think if i could add this as a VM i might be able to run my programmes again.
Problem is I don't know what settings to use, what should i use ase JRE Home directory?
[[IMG]http://lh5.google.co.uk/mrichytech/R67jzgK0k8I/AAAAAAAAAIQ/SwSQTH1Uzyo/s144/add%20JRE.png[/IMG]]("http://picasaweb.google.co.uk/mrichytech/Eclipse/photo#5165316296588694466")


Thanks in anticipation
Tim

---

### Post by chrono_ku on 2008-03-12
Ok, I found a solution:

Window-Preferences

Then, in the java section, select installed JREs

there you add a new JRE and give the corresponding route...

i.e. I have Eclipse installed on /home/chrono/apps/eclipse

I give this route and add the JRE but you should add the route you have installed eclipse in

Then I select it and now I'm ready to debug...

I hope this helps...

---

