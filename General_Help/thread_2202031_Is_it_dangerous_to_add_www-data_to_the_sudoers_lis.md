---
title: "Is it dangerous to add www-data to the sudoers list?"
date: 2014-01-27
forum: General Help
---

### Post by frogwarrior on 2014-01-27
I'm mainly a PHP programmer, so I love being able to use the other languages I'm learning in conjunction with it. I started playing around with initiating shell scripts with PHP. Since theres no password prompt, it can't do anything that requires privileges, so to get around that, I can add this to the sudoers list:
www-data ALL=(user) NOPASSWD: /path/to/script/script.sh
so then I only have to run:

```
shell_exec("sudo -u user /var/www/ss/shell_script.sh");
```

in my PHP files, and I do all kinds of administrative tasks that PHP would never have permission to do. Something tells me this is a massive security vulnerability. Any third party plugins I have installed could gain full access to my system. Is there a way to safely do this? For example, if I were to make apache run use a different username in my sandboxes.

---

### Post by justleen on 2014-01-27
AFAIK this is just fine, as long as you specify a script/command to be run by apache. that way only that command/script can be run. Any third party  will only be able to run that script and nothing else.
This is way better than adding apache to other groups which would allow a lot more other commands/scripts to be run.

An alternative is to have a seperate user run this script, place output in a file readable by apache/php and parse the file with php.

---

### Post by frogwarrior on 2014-01-27
Cheers, I didn't know it was restricted just to this script. I'll stick to this method then. Its amazing the things you can do when you can run shell scripts with PHP.

---

