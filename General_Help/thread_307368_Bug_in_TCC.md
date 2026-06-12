---
title: "Bug in TCC?"
date: 2006-11-26
forum: General Help
---

### Post by solarwind on 2006-11-26
Is there (once again) a bug in tcc? I get some weird error when I try to compile a hello world.c program in tcc, but running it using the tcc interpreter option works perfectly.

---

### Post by jmmcd on 2007-07-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/tcc/+bug/70854](https://bugs.launchpad.net/ubuntu/+source/tcc/+bug/70854) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi Solarwind,

did you ever find out more about this bug? What error message were you seeing? Was it connected with your previous error report and did you fix that one as well? :)

At the moment I'm seeing this:

$ tcc hello.c
tcc: file 'AS_NEEDED' not found
/usr/lib/libc.so:3: filename expected
/usr/lib/libc.so:3: unrecognized file type
/usr/lib/libc.a: '_nl_category_name_idxs' defined twice
[snip]

$ tcc -run hello.c
tcc: file 'AS_NEEDED' not found
/usr/lib/libc.so:3: filename expected
/usr/lib/libc.so:3: unrecognized file type
/usr/lib/libc.a: '_nl_category_name_idxs' defined twice
[snip]

There's been some talk about this or a similar error on the tcc mailing list (google for AS_NEEDED tcc) but I think it's a distro-dependent problem. Anyone know a workaround? 

And btw, how come launchpad is so slow..? :(

---

