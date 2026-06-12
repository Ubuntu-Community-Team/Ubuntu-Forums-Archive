---
title: "GRUB stops upgrade at prompt"
date: 2019-05-08
forum: General Help
---

### Post by Skaperen on 2019-05-08
in an AWS EC2 instance, run by user data bash code, which means there is no terminal available, doing an upgrade gets a new kernel, which requires GRUB to be setup, again.  but GRUB outputs a full screen message and a simple <Ok> prompt.  if i were doing this at a terminal, i could just press the Enter key and move on.  i tried piping in a newline to the apt-get command in the user data bash code, but that does not seem to be inputting anything to whatever is waiting for input.  maybe it opened /dev/tty directly instead of using STDIN which is now a pipe.

any suggestions how to make the GRUB setup move on or give it an empty line of input from in a script with no terminal present?

*edit*:

GRUB is trying to be very interactive, not realizing it's a batch run and no one is there (i connect via ssh to diagnose this).  it is running **whiptail** to display messages and wait for input.  isof shows me that it does have [FONT=courier new]/dev/tty[/FONT] open though i cannot see if it reading it.  i killed **whiptail** a few times but GRUB keeps on interacting.  so i moved **[FONT=courier new]/bin/whiptail[/FONT]** aside and replaced it with a copy of **[FONT=courier new]/bin/true[/FONT]**. and killed **whiptail** one last time.   apparently it finished without installing GRUB.

alternatively, maybe GRUB can be convinced to not do this via some configuration.

---

