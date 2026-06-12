---
title: "Boinc &amp; Conky"
date: 2006-11-19
forum: General Help
---

### Post by maxol on 2006-11-19
I'm running edgy and have boinc installed via synaptic.

Seti runs without problems but I want to use conky to monitor seti.

I have set "# boinc (seti) dir" in .conkyrc to /var/lib/boinc-client/projects/setiathome.berkeley.edu as this seems to be where the seti folder is (there is nothing in my /home directory).

Conky does not display my seti statistics ( ${seti_prog /}
${seti_progbar 12,230 /}$color$color ${voffset -0}${color white}
${seti_credit /} ).

Am I pointing conky at the wrong folder? It seems a little curious that seti can write work units to /var/lib when I'm running boinc as a user?

As I said boinc / seti are running fine but conky can't see them.

Any Ideas?

maxol.

---

