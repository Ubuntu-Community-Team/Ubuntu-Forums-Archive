---
title: "printed sheet left margin offset by two characters"
date: 2020-05-10
forum: General Help
---

### Post by him610 on 2020-05-10
Noticed that when printing text from text editor or lp, the left margin on the printed page was missing the first two characters on the left only with LTS 20.04. Did not occur using LTS 18.04.

Observations:
1. LTS 18.04 could be configured using Generic PCL 5LF resulting in no missing characters on left. 

2. LTS 20.04 was missing capability to use Generic PCL 5LF; however, it was configured with Generic PCL 5 which did result in missing two characters on the left - this occurred on two different computers using LTS 20.04.

---

### Post by him610 on 2020-05-10
I figured something out on this issue.

Corrective action:
1.  In Settings>Printers (system-config-printer) deleted instance of Printer Generic-PCL5-Laser.

2.  Created new printer using Generic-PCL-Laser.

3. Test printed page of text using new Generic-PCL-Laser resulting in NO missing characters on the left. It printed the full 80 characters using lp.

Hope maybe this will help someone with similiar issues. 

All you mothers out there, have a happy 'Mother's Day.'

---

### Post by him610 on 2020-05-14
I think I spoke too soon. 
Printing from a text editor, it appears there is another issue when using Generic-PCL-Laser, there are no line feeds, or line wraps at the right margins so if one has a line that exceeds the width of the page (~94 chars), the characters beyond that are lost. 
Printing using *lp* from the terminal, the line wraps at the right margin as expected on both LTS 18.04 and LTS 20.04. 
I think I am confused now - why one and not the other? Maybe my text editor configuration settings are not quite right....:(

The developers eliminated the configuration for *Generic PCL 5LF * in LTS 20.04 which I always used for the past ten or so years for my Dell 1700N laser printer. 
How do I get it back?
Does anyone have any thoughts on this?

---

