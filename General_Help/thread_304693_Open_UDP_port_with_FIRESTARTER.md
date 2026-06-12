---
title: "Open UDP port with FIRESTARTER"
date: 2006-11-22
forum: General Help
---

### Post by ghepardo on 2006-11-22
Hi,
How can I open an UDP port with firestarter?! It seems it allows to open only TCP ports.

Someone knows how to open UDP ones!?

And also, I have another question: does the firewall runs and protect my pc also when the GUI isn't turned on!? (that is, the icon is not on the systray).

---

### Post by wieman01 on 2006-11-22
1. It should open both UDP & TCP... What makes you think it only opens TCP?
2. The firewall runs also if the GUI is turned off. Firestarter runs as process in the background. The GUI only serves the purpose of being a nice tool to configure Firestarter.

---

### Post by ghepardo on 2006-11-22
> **wieman01 said:**
> 1. It should open both UDP & TCP... What makes you think it only opens TCP?
2. The firewall runs also if the GUI is turned off. Firestarter runs as process in the background. The GUI only serves the purpose of being a nice tool to configure Firestarter.

Well I opened 2 port for amule. The firewall, in the events tab, gives me HITS in the UDP port of amule, si I thought it wasn't opened.

---

### Post by wieman01 on 2006-11-22
Ok, I am not using UDP so I am not sure... However, since there is no option I assume it makes no difference. Let's see what the documentation says.

---

### Post by ghepardo on 2006-11-22
> **wieman01 said:**
> Ok, I am not using UDP so I am not sure... However, since there is no option I assume it makes no difference. Let's see what the documentation says.

Well I checked the DOCS on the internet, but they does not specify the protocol when speaking about policies.

---

### Post by wieman01 on 2006-11-22
The documentation does not say anything. But try this:
> su root
Enter your root password.
> cat /etc/firestarter/outbound/setup
There should be two lines:
> $IPT -A OUTBOUND -p **[COLOR="Red"]tcp[/COLOR]** -s $target --dport $port -j ACCEPT
$IPT -A OUTBOUND -p **[COLOR="Red"]udp[/COLOR]** -s $target --dport $port -j ACCEPT
Both appear under "permissive" and "restrictive" policy, so I really think both UDP and TCP are opened once you have configured your firewall accordingly & "allowed a service".

---

### Post by ghepardo on 2006-11-22
> **wieman01 said:**
> The documentation does not say anything. But try this:

Enter your root password.

There should be two lines:

Both appear under "permissive" and "restrictive" policy, so I really think both UDP and TCP are opened once you have configured your firewall accordingly & "allowed a service".

Thanks, but this is the outbound traffic code, mine is an inbound rule

---

### Post by wieman01 on 2006-11-22
Well, same should apply to inbound traffic. Check this file:
> cat /etc/firestarter/inbound/setup
This script:
> # Initialize
$IPT -N INBOUND 2> /dev/null
$IPT -F INBOUND

# Temoporarily set the field separator for CSV format
OLDIFS=$IFS
IFS=','

# Allow response traffic
$IPT -A INBOUND -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A INBOUND -p udp -m state --state ESTABLISHED,RELATED -j ACCEPT

# Hosts from which connections are always allowed
while read host garbage
        do
                $IPT -A INBOUND -s $host -j ACCEPT
        done < /etc/firestarter/inbound/allow-from

# Services allowed
while read service ports target garbage
        do
                IFS=' '
                for port in `echo $ports`; do
                        scrub_parameters
                        case "$port" in
                          # Override broadcast blocking for Samba share discovery
                          "1900" ) $IPT -I INPUT -p tcp -s $target --dport 1900 -j ACCEPT
                                   $IPT -I INPUT -p udp -s $target --dport 1900 -j ACCEPT;;
                          # Default service handler
                          * ) $IPT -A INBOUND -p tcp -s $target --dport $port -j ACCEPT
                              $IPT -A INBOUND -p udp -s $target --dport $port -j ACCEPT;;
                        esac
                done
                IFS=','
        done < /etc/firestarter/inbound/allow-service

$IPT -A INBOUND -j LSI
# Restore system field separator
IFS=$OLDIFS

---

### Post by ghepardo on 2006-11-22
Thank you.

---

