---
title: "Unable to print with Java"
date: 2006-11-12
forum: General Help
---

### Post by msumurph on 2006-11-12
When my Java applications try to print I get a dialog with the message, "No print service found." :( 

I have searched for a while but have not found any specific solutions.  It seems to have something to do with the way Java communicates with CUPS.

I am running Edgy with sun-java5 installed. I am able to print from other applications, but not from any Java applications, such as NetBeans.

Any help would be appreciated.

Thanks!

---

### Post by msumurph on 2006-11-13
SOLVED:

After more searching, I discovered a [faq]("http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux#Why_do_I_get_a_.22No_print_service_found.22_whenever_I_attempt_to_print.3F") for FreeMind that discusses this problem.


I renamed the symbolic link **/usr/lib/libcups.so** to **/usr/lib/libcups-old.so** and Viola!, my Java Apps can print! :-D

---

### Post by json684 on 2006-11-19
You have solved my problem!!! Thank you very much.

---

### Post by Merlin 3 on 2007-05-28
> **msumurph said:**
> SOLVED:

After more searching, I discovered a [faq]("http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux#Why_do_I_get_a_.22No_print_service_found.22_whenever_I_attempt_to_print.3F") for FreeMind that discusses this problem.


I renamed the symbolic link **/usr/lib/libcups.so** to **/usr/lib/libcups-old.so** and Viola!, my Java Apps can print! :-D

Any chance of explaining where you renamed exactly..where do you find the symbolic link?
Many thanks

---

### Post by t0mc4t on 2007-06-07
Hello..

I do have the same problem here..
Would you please tell us exactly what you did, so we can solve the problem?
Many thanks...

---

### Post by t0mc4t on 2007-06-08
Anyone? Help Please...

---

