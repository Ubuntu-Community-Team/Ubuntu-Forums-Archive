---
title: "pkill fails ... no error message"
date: 2019-12-08
forum: General Help
---

### Post by Skaperen on 2019-12-08
it was suggested to me that i should use [COLOR=#0000cd][FONT=courier new]**pkill -u**[/FONT][/COLOR] to kill a user (when done as root), and also for the user to kill all her own processes, including the background processes that Xfce logout leaves running.

1.  does [COLOR=#0000cd][FONT=courier new]**pkill**[/FONT][/COLOR] skip itself in the kill list and also mask [COLOR=#b22222][FONT=courier new]**SIGHUP**[/FONT][/COLOR] or all signals so it can always complete all the kills?  i tried it once and it did kill all the processes, then.  but i don't know if it takes all the needed steps to be sure it always works that way.

2.  the [COLOR=#0000cd][FONT=courier new]**pkill**[/FONT][/COLOR] man page showed ... after users, suggesting it can kill more than 1 at a time.  so i tried [COLOR=#0000cd][FONT=courier new]**pkill -u**[/FONT][/COLOR] (as root) with 2 users and neither was killed.  also, there were no error messages.  shouldn't there be at least one error message or maybe just kill the first user? 

i was going to create an alias of [COLOR=#0000cd][FONT=courier new]**pkill -u**[/FONT][/COLOR] as [COLOR=#0000cd]**ku**[/COLOR], but maybe not now.

---

### Post by Holger_Gehrke on 2019-12-09
See the man page ('man pkill'):
> The running pgrep or pkill process will never report itself as a match.
Since pkill doesn't report processes but sends signals to them instead, I read this as "it won't send signals to itself".
>        -u, --euid euid**[COLOR=#ff0000],[/COLOR]**...
              Only match processes whose effective user ID is listed.  Either the numerical or symbolical value may be used.

       -U, --uid uid**[COLOR=#ff0000],[/COLOR]**...
              Only match processes whose real user ID is listed.  Either the numerical or symbolical value may be used.
The list of user-ids is comma-separated (and - as usual - must not contain spaces).

Holger

---

### Post by Skaperen on 2019-12-09
> **Holger_Gehrke said:**
> See the man page ('man pkill'):

as mentioned in post #1, i did.

> **Holger_Gehrke said:**
> Since pkill doesn't report processes but sends signals to them instead, I read this as "it won't send signals to itself".

however, when it kills the the holder of the pty end of its controlling tty, it can receive a SIGHUP.  it needs to mask or handle that to avoid the default behavior.  i don't know whether it does this much or not.  if not, then i cannot trust that it will kill all the processes since the syscall only signals one process at a time.

> **Holger_Gehrke said:**
> The list of user-ids is comma-separated (and - as usual - must not contain spaces).

that's obscure in my man page for pkill.  it needs to be stated verbosely.

---

### Post by Holger_Gehrke on 2019-12-10
'pgrep' and 'pkill' are actually the same program (pkill is a symbolic link). It's part of the package 'procps' and a look at that package with 'apt show procps' tells me that the homepage for that project is [https://gitlab.com/procps-ng/procps](https://gitlab.com/procps-ng/procps) . For corner cases like the one you're interested in, looking at the source is probably the best method of making certain of the behaviour of a program. I am not really good with C, but I don't see any signal-handling in pgrep.c, so it probably will terminate on SIGHUP unless I missed something.

The comma as separator is shown in the description of the option, the prohibition against spaces in the list doesn't originate with pgrep / pkill itself but with the shell which will split the command line into tokens at all white space characters; the list would get split into two separate entries in the array of arguments passed to the program if there was a space in it. Also the second example in the DESCRIPTION-section of the man-page is 'pgrep -u root,daemon' - it doesn't get much more verbose and obvious than that in a man-page ...
Holger

---

### Post by Skaperen on 2019-12-11
i need to see if there is a way i can [COLOR=#b22222][FONT=courier new]**strace**[/FONT][/COLOR] [COLOR=#0000cd][FONT=courier new]**pkill**[/FONT][/COLOR] with [COLOR=#0000cd][FONT=courier new]**strace**[/FONT][/COLOR] running as [COLOR=#006400][FONT=courier new]**root**[/FONT][/COLOR] and [COLOR=#0000cd][FONT=courier new]**pkill**[/FONT][/COLOR] running as the user to kill and see what syscalls it actually does.  that would be easier than reading _someone else's source code_.

---

