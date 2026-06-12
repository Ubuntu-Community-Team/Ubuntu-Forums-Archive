---
title: "Urgent question for anyone who works with python CGI"
date: 2006-08-04
forum: General Help
---

### Post by boom2k1 on 2006-08-04
I have a HTML file containing a form that when submit it would run a python script.
What it is supposed to do is to execute on my computer so it would do something. However, when I press the submit button, it prompts me to download the form instead of automatically running on the background and executing stuff!

How do you make it to execute instead of prompting the Open Save option?

---

### Post by scxtt on 2006-08-04
you have to enable (ExecCGI) for the directory you're running the script from, and you have to let apache know that .py files are scripts ...

---

### Post by boom2k1 on 2006-08-05
How do you do that?

---

### Post by scxtt on 2006-08-06
edit your /etc/apache2/apache2.conf, uncomment the line that allows you to use your home directory as a hosting area and add ExecCGI to another line in the UserDir area ... i'd get more specific, but i don't have apache2 installed right now and don't feel like installing it presently ...

---

