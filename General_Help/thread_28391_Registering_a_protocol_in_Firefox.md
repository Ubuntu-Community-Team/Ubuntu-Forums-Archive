---
title: "Registering a protocol in Firefox"
date: 2005-04-20
forum: General Help
---

### Post by aaroniu on 2005-04-20
Upon clicking on a telnet:// link in Firefox 1.0.2, I get the message "telnet is not a registered protocol." In my Advanced Preferences I see the line:

applications.telnet     default     string     xterm -e telnet %h %p

Which looks right, but that's about as far as my proficiency allows me to track this.

Is this a Firefox issue, or do I have to set up what to do with telnet:// links somewhere in Ubuntu? If so, where?

---

### Post by aaroniu on 2005-04-21
This would, I guess, apply to other protocols like news:// etc. Is there a config file somewhere with all of this data?

---

### Post by banadushi on 2005-04-22
go into ~/.mozilla/firefox/[profile] and add a file called user.js if its not already there.  Then you can add lines like:

user_pref("network.protocol-handler.app.telnet", "~/bin/sshin.bash");
user_pref("network.protocol-handler.external.telnet", true);

to set the handler and enable it.  There is also a way to do it through firefox itself, about:preferences I think, but dont' quite me on that one!

Have fun

Jason

---

