---
title: "Ubuntu 16:04.1 : Firefox High CPU usage on Google search page"
date: 2017-02-12
forum: General Help
---

### Post by molinaro on 2017-02-12
Since I upgraded from 14:04 to 16:04.1  I have been noticing that every time I use Google search, Firefox uses 70% of the CPU, circa. This happens only when a Google search result page is loaded in my browser and with no other Google service. As I understand, the majority of the CPU's cycles are used by omni.ja (AKA Web Content) plug-in, ex omni.jar. In the past, this plug-in was affected by a bug which  caused an abnormal CPU usage. Unfortunately I cannot find the informations I had about this bug.
I checked on another machine where Ubuntu 16:10 is installed and I can confirm that this anomaly is not present. 

Thanks for your help

---

### Post by molinaro on 2017-02-13
I restarted Firefox in safe mode with a tab displaying a Google search page and the issue seem to be resolved. 
I left this reply in case someone has the same problem.

---

### Post by vasa1 on 2017-02-13
> **molinaro said:**
> I restarted Firefox in safe mode with a tab displaying a Google search page and the issue seem to be resolved. 
I left this reply in case someone has the same problem.

So is the solution to use safe mode when doing a Google search? Could you please clarify in a little more detail if you meant something else?

---

### Post by carsten-br on 2017-11-29
I had the same issue just now, the given solution worked for me. 

Steps to reproduce:

0. Close Firefox.
1. Open Firefox in safe mode, i.e. via Terminal: firefox -safe-mode
2. Visit [www.google.com]("http://www.google.com")
3. Agree to privacy reminder (important!)
4. Search for something
5. Stay on search results page until CPU-usage goes down (few seconds in my case)
6. Close Firefox
7. Open Firefox normally
8. Visit [www.google.com](www.google.com)
9. Confirm privacy reminder (important!)
10. Search for something.

Google search results page should have low CPU consumption now.

---

