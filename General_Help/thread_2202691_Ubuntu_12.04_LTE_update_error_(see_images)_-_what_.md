---
title: "Ubuntu 12.04 LTE update error (see images) - what does this mean and how do I fix it?"
date: 2014-01-30
forum: General Help
---

### Post by bullwinkle2 on 2014-01-30
I get the red warning triangle and this warning:

[IMG]http://s14.postimg.org/vybghvjm7/Ubuntu_error_message.png[/IMG]

When I did as instructed and clicked on "Check for updates" I got this:

[IMG]http://s9.postimg.org/dabsd71j3/Ubuntu_error_message_2.png[/IMG]

The full text in the text box reads:

W:Failed to fetch bzip2:/var/lib/apt/lists/partial/mirror.team-cymru.org_ubuntu_dists_precise-updates_main_source_Sources  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/mirror.team-cymru.org_ubuntu_dists_precise-updates_universe_source_Sources  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I haven't changed anything on this system and never had this problem before.  The network connection is working fine, so that's not the issue.  How do I fix this?

---

### Post by balaam.p on 2014-01-30
It looks like some of the links in the repository are defunked. Try another Mirror in Synaptic, if it still won't work it might be those links are no longer active so go to Synaptic and Settings>Repositories and in the Other Software tab untick the links and try again.

---

### Post by bullwinkle2 on 2014-01-30
That was the problem, apparently.  Now it is installing 220 updates!  Wonder how long it has been like that and I didn't notice?

Thanks!

---

