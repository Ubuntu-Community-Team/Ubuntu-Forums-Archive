---
title: "Cursor keys stop working for less (pager)"
date: 2008-05-25
forum: General Help
---

### Post by heathd on 2008-05-25
Hi,

I have random intermittent problems with the 'less' pager command. Normally when I use less, I can use cursor keys to scroll up and down the document. However, sometimes when I pipe the output of a command to less, the cursor keys stop working. In this scenario, when I press a cursor key instead of scrolling the document, the string ^[OB or ^[OA appears at the : prompt. 

I tried looking at environment variable settings such as the TERM environment variable, but couldn't think of anything which would cause this behaviour. Has anyone got any ideas?

thanks

David

---

### Post by heathd on 2008-05-27
I think I figured it out. For some reason the php script I was running was reading from STDIN and therefore the STDIN was getting sent through to that rather than 'less'. The solution was to redirect /dev/null to the scripts STDIN.

php script.php < /dev/null | less

---

