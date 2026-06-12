---
title: "Mutt &amp; Muttprint"
date: 2005-10-11
forum: General Help
---

### Post by jevb on 2005-10-11
I have Mutt & Muttprint installed. Mutt is version "1.5.6+20040907i (CVS)" from Ubuntu repository. Muttprint is version 0.72c. I don't remember which repository it is from, but it was installed with Synaptic. In my muttrc file, the print command points to /usr/bin/muttprint, which is where muttprint is located. Here's the problem, every time I try to print from Mutt I get this error message:

"Muttprint Version 0.72c -- Error
======================================================================

Line 624: Latex didn't work. There's no DVI file. If you write a
bugreport, please include a mail where printing fails."

Here's lines 617 to 627 of the muttprint script:

#
# running latex twice because of the "page ... of ..."
system("latex -interaction=nonstopmode mail.tex >> $errorRedirection 2>&1");
system("latex -interaction=nonstopmode mail.tex >> $errorRedirection 2>&1");

#
# no check of the exit code because we do this here
unless (-e $Temp{dvi}) {
	fatalError "Latex didn't work. There's no DVI file. If you ".
		"write a bugreport, please include a mail where printing fails.";
}
---------------------------------------------------------------------------------------------------
End of script.

Does anybody know what I need to install to make this work? I have already installed every package that looks related. 

Thanks

---

