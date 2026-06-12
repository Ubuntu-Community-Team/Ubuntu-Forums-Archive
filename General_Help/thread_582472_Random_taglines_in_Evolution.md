---
title: "Random taglines in Evolution"
date: 2007-10-19
forum: General Help
---

### Post by gjtoth on 2007-10-19
Just a quick question to perhaps stop the whining as to how terrible Gutsy installs are :)

Has anyone tried getting random taglines into their email whilst using Evolution?  There are just a couple of things that are keeping me from using it all the time and that's one of 'em.

---

### Post by gjtoth on 2007-10-20
I got it figured out with a little help from the bash scripting sites.

Here's what I did.  I installed TaRT and got it running the way it should.  Then, wrote a script that runs TaRT to generate a signature with a random tagline, date & time and whatever else I want to throw in there.  I also use TaRT to generate a signature for Thunderbird so when I run the script, it uses a second configuration file just for Evolution.  The script then reads the output of TaRT and places it in the email.  The script is:

#!/bin/bash
tart --config .tartrc2
echo "<div>-- </div>"
cat ~/.signature2

The echo line simple puts a couple of dashes above the signature.

---

