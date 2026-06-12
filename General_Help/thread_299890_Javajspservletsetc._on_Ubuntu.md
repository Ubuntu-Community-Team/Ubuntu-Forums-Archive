---
title: "Java/jsp/servlets/etc. on Ubuntu"
date: 2006-11-14
forum: General Help
---

### Post by fractalvibes on 2006-11-14
I have a need to learn java, learn jsp and servlets,etc.  I've gone a fraction of the way down the path of learning 'hello world' on my Win XP machine and think it is a good thing to try also on this little Ubuntu machine.

Forgive my ignorance - I write VBA or ASP code by day and dabble with PHP on the side.

1.)  On Win platform I have the JDK and can use javac to compile  - what is available via synaptic to accomplish the same?

2.) Haven't got this far yet, but to progress beyond writing simple stand-alone java stuff into writing server-side jsp and servlets, I need something called Apache Tomcat (I suppose equivalent to the ASP worker process that IIS hands off ASP requests to handle?)  or perhaps something called JBoss (a web server unto itself?)

Any thoughts, synaptic "shopping lists", etc. most appreciated.  Itty bitty 333 mhz system, yet I am amazed at all Ubuntu can do given the limited resources available.  

thanks,

fv

---

### Post by mark2741 on 2006-11-14
I've read a lot of complaints on the forums about people having trouble installing the JDK (which is what you need to have installed in order to get the java binaries that you need, like the javac compiler). I remember briefly trying to install it via a direct download of the JDK from Sun's site and ran into some trouble. I then did a search on this forum and found out that Automatix can install and configure the JDK, so that's what I've done. It works like a charm. I suggest you just do that. Just remember that you'll need the JDK and not the JRE.

As for Tomcat: Tomcat is a "Servlet Container" (a 'servlet' is another term for java code that runs on a server). It is most commonly referred to as an Application Server. An Application Server serves up Java. In what way (ie, JSP only, or Applets only, or Java classes (ie, programs), I don't exactly know for sure but I believe it is classes/programs. You need an App Server like Tomcat in order to deploy your java programs to the web. JBoss works similarly to Tomcat and I remember reading that it was based on Tomcat originally. I know that the grad school I'm attending for the java cert teaches using JBoss. I also know that the company I work for, whose flagship web app is written entirely in java, keeps stats on what app servers are customers use. Over half are using Tomcat. Very few are using JBoss. The rest are using ERP-specific app servers such as WebSphere (IBM) or NetWeaver (SAP) or OC4J (oracle).

Hopefully an experienced java developer will come along and confirm what I've stated and/or add to it, as I myself am in the process of learning Java and am midway through a 3-course Java Programming certification at a local grad school. I'm going to take an elective that focuses on JSP in February. Up to this point it's been learning OOP, syntax, and now in the current course the major API classes that are most used. My instructor is terrible and has made learning java much harder, but all in all I've learned a lot and java is a very cool language. I'm thrilled that it is now being open-sourced and hopefully we'll see more acceptance of it in the Ubuntu/Linux community.

---

### Post by fractalvibes on 2006-11-14
Many thanks for the quick response, Mark!  I may aleady have the JDK 
installed and had found something called mmake which is purported to use
javac...we shall see.

thanks again,

fv

---

