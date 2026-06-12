---
title: "[SOLVED] Removing duplicate items from a list"
date: 2007-08-19
forum: General Help
---

### Post by arsenic23 on 2007-08-19
Ok, to preface, I have no experience with sed and awk, though I recently discovered that arguments I can give the rename command often work with sed.

ANYWAY, I have a large list of IP addresses that I've outputed from a firewall log on a windows box.  I was able to use some simple bash scripting to turn the logs into just a list of the IPs with no ports on the end of other unneeded text.  Unfortunately I can't quite figure out who to take this list and remove duplicate entries from it.  I thought I could sort it and then put an if statement inside a loop that checks each line against the one that came before it, but even if that was a good idea ( and I'm not sure it was ), I'm obviously doing something wrong.

Any help would be appriciated.

---

### Post by daveshields on 2007-08-19
If you have a file, say with name f, that has one line for each IP address, then you can get a list of the unique IP addresses with the shell commands:
  $  sort  < f | uniq
You can save the results to a file g by putting "> g" after the "uniq."

If the IP addresses are in a particular column, then you can run the "cut" command before the sort. Or, as you suggest, you could run "sed" before the "sort" command to build the list of lines with the IP addresses.

You can also do this using any language that supports associative arrays (arrays where you can index by any string, not just by an integer). So you have a loop of the form

  for each IP
    table(IP) = 1
and then list the domain of the table.

Such languages include awk, perl, php and python.

---

### Post by arsenic23 on 2007-08-19
Awsome, thank you.
DId not know there was a uniq command.  That makes everything very easy.  

Anyway, thanks again.

---

