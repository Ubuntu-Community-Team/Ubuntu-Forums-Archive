---
title: "Executing a jar file"
date: 2021-01-11
forum: General Help
---

### Post by rfresh737 on 2021-01-11
I'm using B4J to build a Java application. They provide a B4J app to help us port our jar file over to the Mac and to Linux. I'm developing on a Windows machine.

I successfully ported over to the Mac and there are supporting folders and a run.command that will let you run your jar file as a self contained package. The user doesn't have to worry about installing Java. On the Mac I click on the run.command and my app starts up.

The build process is similar on Linux. I do the build and end with similar folders and a run.command. However, double clicking on the run.command does not start up my jar file. I'm wondering if this run.command is just for the Mac? or if there is such a thing in Linux?

Thank you...

---

### Post by &amp;KyT$0P# on 2021-01-11
> **rfresh737 said:**
> However, double clicking on the run.command does not start up my jar file. 

What if you open a Terminal in the directory containing the run.command file, and run [FONT=Courier New]./run.command[/FONT] in that Terminal?

---

### Post by rfresh737 on 2021-01-11
Hmmm...it does run that way. So that's the only way to run it? I have to open a terminal window and run that command?

---

### Post by CelticWarrior on 2021-01-11
> **rfresh737 said:**
> Hmmm...it does run that way. So that's the only way to run it? I have to open a terminal window and run that command?

No, you can double-click as well provided that:
[LIST=1]
[*]Your file is marked as executable -> righty-click > Properties > Permissions tab...
[*]Your file manager is set to execute or at least ask what to do -> Preferences > Behavior
[/LIST]

---

### Post by rfresh737 on 2021-01-11
Got it...that worked when I set it up in file manager.

Much thanks...

---

### Post by CelticWarrior on 2021-01-11
You're welcome.

If you consider this issue/question solved to your satisfaction please use the thread tools at the top of the page to mark as such.

---

