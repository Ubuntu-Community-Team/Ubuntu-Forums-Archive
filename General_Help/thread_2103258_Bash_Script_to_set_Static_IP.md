---
title: "Bash Script to set Static IP"
date: 2013-01-09
forum: General Help
---

### Post by greavette on 2013-01-09
Hello,

I'm looking for a Bash Script that will prompt the user running the script to ask for the particulars (IP Address, Netmask, Gateway, etc) which will then update the /etc/networking/interfaces file to make the server a static ip.

Anyone seen something like this floating around I can use?

Thank you.

---

### Post by ivicks on 2013-01-09
The only issue I see with using a script is your would need it to change interfaces, resolv.conf, uninstall dhcp-client/dhcp-client3 and then restart /etc/init.d/networking restart
I would rather do this by hand just to make sure nothing weird happened during configuration.

Here is a link to a site with what you would need to do if you wanted to create a script [http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/]("http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/")

---

