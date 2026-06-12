---
title: "firewall-insserv"
date: 2018-05-31
forum: General Help
---

### Post by Freiklite on 2018-05-31
Hi,
On  my PC I use Jessie-debian  and Ubuntu 16-04 LTS .
On jessie the firewall "/etc/init.d/mon_parefeu" works after running 
```
# chmod +x /etc/init.d/mon_parefeu
``````
# insserv mon_parefeu

```

The firewall is
 ```

#!/bin/sh
### BEGIN INIT INFO
# Provides:           mon_parefeu
# Required-Start:     $local_fs
# Should-Start:
# Required-Stop:      $local_fs
# Should-Stop:
# X-Start-Before:     $network
# X-Stop-After:       $network
# Default-Start:      S
# Default-Stop:       0 6
# Short-description:  Configure le parefeu
# Description:        Met en place les règles iptables.
### END INIT INFO
   
   #------------------------Explications----------------------------------#
   #
   # Défauts :
   # - Cette configuration s'applique à toutes les interfaces réseau.
   #   Si vous voulez restreindre cela à une interface donnée,
   #   utilisez '-i INTERFACE' dans la variables $IPTABLES.
   #
   # - Par défaut, le script autorise tout en sortie.
   #   Pour changer ce comportement veuillez indiquer les numéros
   #   de port en question dans les variables
   #            $REMOTE_TCP_SERVICES
   #   et/ou    $REMOTE_UDP_SERVICES
   #
   # - Pour configurer une machine routeur,
   #   changez la valeur de la variable
   #   ISROUTERNAT à true, ainsi que
   #   les interfaces ethx et ethy selon votre configuration
   #         ethx correspond à l'interface du LAN
   #         ethy correspond à l'interface reliée à la truc-box
   #
   # description: Active/Désactive le pare-feu au démarrage
   #
   #----------------------------------------------------------------------#
   
   . /lib/lsb/init-functions
   
   #------------------------VARIABLES-------------------------------------#
   # Mettre à 1 si vous utilisez IPV6 :
   IPV6=1
   # Services que le système offrira au réseau, à séparer avec des espaces
   # ftp : 21, ssh : 22, serveur web : 80, cups : 631, jabber : 5222
   TCP_SERVICES=""
   UDP_SERVICES=""
   # Services que le système utilisera du réseau
   # (défaut : autorise tout en sortie)
   REMOTE_TCP_SERVICES=""
   REMOTE_UDP_SERVICES=""
   
   # Pour une machine faisant office de routeur avec NAT,
   # changer la valeur de la variable ISROUTERNAT à true.
   ISROUTERNAT=false
   # ethx correspond à l'interface du LAN
   # ethy correspond à l'interface reliée à la truc-box
   ethx="eth1"
   ethy="eth0"
   
   # Chemins vers iptables
   readonly IPTABLES=/sbin/iptables
   readonly IP6TABLES=/sbin/ip6tables
   #----------------------------------------------------------------------#
   
   if ! [ -x $IPTABLES ]; then
       exit 0
   fi
   
   if [ $IPV6 -eq 1 ]; then
       if ! [ -x $IP6TABLES ]; then
           exit 0
       fi
   fi
   
   
   #----------------------------FONCTIONS---------------------------------#
   fw_start () {
       
   # Vidage
       fw_clear
       # Parefeu - Suppression des règles
           
   # Interdictions
       $IPTABLES -t filter -P INPUT DROP
       $IPTABLES -t filter -P FORWARD DROP
       $IPTABLES -t filter -P OUTPUT DROP
       
       # Parefeu - interdictions générales établies
       
   # Loopback
       $IPTABLES -t filter -A INPUT -i lo -j ACCEPT
       
   # Trafic d'entrée :
       $IPTABLES -t filter -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
       $IPTABLES -t filter -A INPUT -m state --state ESTABLISHED -j ACCEPT # pour vlc
       $IPTABLES -t filter -A INPUT -p udp -s 212.27.38.253 -j ACCEPT # pour vlc
 
       
   # Refus du ping pour éviter de répondre aux scans des éventuels vilains
       $IPTABLES -t filter -A INPUT -p icmp -j LOG
       $IPTABLES -t filter -A INPUT -p icmp -j DROP
       
   # Sortie autorisée, si aucun port autorisé en sortie n'est défini
           if [ -z "$REMOTE_TCP_SERVICES"] && [ -z "$REMOTE_UDP_SERVICES" ]; then
               $IPTABLES -t filter -P OUTPUT ACCEPT
           fi
       $IPTABLES -t filter -A OUTPUT -m state ! --state INVALID -j ACCEPT # pour vlc
       
   # Services à autoriser en entrée
       for PORT in $TCP_SERVICES; do
           $IPTABLES -A INPUT -p tcp --dport ${PORT} -j ACCEPT
       done
       
       for PORT in $UDP_SERVICES; do
           $IPTABLES -A INPUT -p udp --dport ${PORT} -j ACCEPT
       done
       
   # Services à autoriser en sortie
       
       for PORT in $REMOTE_TCP_SERVICES; do
           $IPTABLES -A OUTPUT -p tcp --dport ${PORT} -j ACCEPT
       done
       for PORT in $REMOTE_UDP_SERVICES; do
           $IPTABLES -A OUTPUT -p udp --dport ${PORT} -j ACCEPT
       done
       # Parefeu - Mise en place des règles
       
       if $ISROUTERNAT ; then
           $IPTABLES -A INPUT -i $ethx -j ACCEPT
           $IPTABLES -A INPUT -p icmp -j ACCEPT
           $IPTABLES -A FORWARD -i $ethy -o $ethx -m state --state RELATED,ESTABLISHED -j ACCEPT
           $IPTABLES -A FORWARD -o $ethy -j ACCEPT
           $IPTABLES -t nat -A POSTROUTING -o $ethy -j MASQUERADE
           # Parefeu - Routeur avec NAT
       fi
       
   # Toutes les autres connexions sont enregistrées dans syslog
       $IPTABLES -t filter -A INPUT -j LOG --log-level=4
   
   # Configuration IPV6
       if [ $IPV6 -eq 1 ]; then
       # Interdictions
           $IP6TABLES -t filter -P INPUT DROP
           $IP6TABLES -t filter -P FORWARD DROP
           $IP6TABLES -t filter -P OUTPUT DROP
           
       # Loopback
           $IP6TABLES -t filter -A INPUT -i lo -j ACCEPT
           
       # Trafic d'entrée :
           $IP6TABLES -t filter -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
           
       # Refus du ping pour éviter de répondre aux scans des éventuels vilains
           $IP6TABLES -t filter -A INPUT -p icmp -j LOG
           $IP6TABLES -t filter -A INPUT -p icmp -j DROP
           
       # Sortie autorisée, si aucun port autorisé en sortie n'est défini
               if [ -z "$REMOTE_TCP_SERVICES"] && [ -z "$REMOTE_UDP_SERVICES" ]; then
                   $IP6TABLES -t filter -P OUTPUT ACCEPT
               fi
           
       # Services à autoriser en entrée
           for PORT in $TCP_SERVICES; do
               $IP6TABLES -A INPUT -p tcp --dport ${PORT} -j ACCEPT
           done
           
           for PORT in $UDP_SERVICES; do
               $IP6TABLES -A INPUT -p udp --dport ${PORT} -j ACCEPT
           done
           
       # Services à autoriser en sortie
       
           for PORT in $REMOTE_TCP_SERVICES; do
               $IP6TABLES -A OUTPUT -p tcp --dport ${PORT} -j ACCEPT
           done
           for PORT in $REMOTE_UDP_SERVICES; do
               $IP6TABLES -A OUTPUT -p udp --dport ${PORT} -j ACCEPT
           done
           # Parefeu - Mise en place des règles
       
           if $ISROUTERNAT ; then
               $IP6TABLES -A INPUT -i $ethx -j ACCEPT
               $IP6TABLES -A INPUT -p icmp -j ACCEPT
               $IP6TABLES -A FORWARD -i $ethy -o $ethx -m state --state RELATED,ESTABLISHED -j ACCEPT
               $IP6TABLES -A FORWARD -o $ethy -j ACCEPT
               $IP6TABLES -t nat -A POSTROUTING -o $ethy -j MASQUERADE
               $IP6TABLES -A INPUT -p icmpv6 --icmpv6-type router-solicitation -m hl --hl-eq 255 -j ACCEPT
               $IP6TABLES -A OUTPUT -p icmpv6 --icmpv6-type router-advertisement -j ACCEPT
           fi
           
           # Pour toute interface de type broadcast
           $IP6TABLES -A INPUT -p icmpv6 --icmpv6-type neighbour-solicitation -m hl --hl-eq 255 -j ACCEPT
           $IP6TABLES -A INPUT -p icmpv6 --icmpv6-type neighbour-advertisement -m hl --hl-eq 255 -j ACCEPT
           $IP6TABLES -A OUTPUT -p icmpv6 --icmpv6-type neighbour-solicitation -j ACCEPT
           $IP6TABLES -A OUTPUT -p icmpv6 --icmpv6-type neighbour-advertisement -j ACCEPT
   
   
       # Toutes les autres connexions sont enregistrées dans syslog
           $IP6TABLES -t filter -A INPUT -j LOG --log-level=4
       fi
   }
   
   fw_stop () {
       #$IPTABLES -F
       #$IPTABLES -t nat -F
       #$IPTABLES -t mangle -F
       #$IPTABLES -P INPUT DROP
       #$IPTABLES -P FORWARD DROP
       #$IPTABLES -P OUTPUT ACCEPT
       iptables-save > /etc/firewall
   }
   
   fw_clear () {
       $IPTABLES -t filter -F
       $IPTABLES -t nat -F
       $IPTABLES -t mangle -F
       $IPTABLES -t raw -F
       $IPTABLES -t filter -P INPUT ACCEPT
       $IPTABLES -t filter -P OUTPUT ACCEPT
       $IPTABLES -t filter -P FORWARD ACCEPT
       $IPTABLES -t nat -P PREROUTING ACCEPT
       $IPTABLES -t nat -P POSTROUTING ACCEPT
       $IPTABLES -t nat -P OUTPUT ACCEPT
       $IPTABLES -t mangle -P PREROUTING ACCEPT
       $IPTABLES -t mangle -P OUTPUT ACCEPT
       $IPTABLES -t mangle -P POSTROUTING ACCEPT
       $IPTABLES -t mangle -P FORWARD ACCEPT
       $IPTABLES -t mangle -P INPUT ACCEPT
       $IPTABLES -t raw -P OUTPUT ACCEPT
       $IPTABLES -t raw -P PREROUTING ACCEPT
       $IPTABLES -F
       if [ $IPV6 -eq 1 ]; then
           $IP6TABLES -t filter -F
           $IP6TABLES -t nat -F
           $IP6TABLES -t mangle -F
           $IP6TABLES -t raw -F
           $IP6TABLES -t filter -P INPUT ACCEPT
           $IP6TABLES -t filter -P OUTPUT ACCEPT
           $IP6TABLES -t filter -P FORWARD ACCEPT
           $IP6TABLES -t nat -P PREROUTING ACCEPT
           $IP6TABLES -t nat -P POSTROUTING ACCEPT
           $IP6TABLES -t nat -P OUTPUT ACCEPT
           $IP6TABLES -t mangle -P PREROUTING ACCEPT
           $IP6TABLES -t mangle -P OUTPUT ACCEPT
           $IP6TABLES -t mangle -P POSTROUTING ACCEPT
           $IP6TABLES -t mangle -P FORWARD ACCEPT
           $IP6TABLES -t mangle -P INPUT ACCEPT
           $IP6TABLES -t raw -P OUTPUT ACCEPT
           $IP6TABLES -t raw -P PREROUTING ACCEPT
           $IP6TABLES -F
       fi
   }
   
   fw_status () {
       $IPTABLES -L --line-numbers
       if [ $IPV6 -eq 1 ]; then
           $IP6TABLES -L --line-numbers
       fi
   }
   
   #----------------------------------------------------------------------#
   
   case "$1" in
       start|restart)
           log_daemon_msg "Starting firewall.."
           fw_start
           log_end_msg $?
       ;;
       stop)
           log_daemon_msg "Stopping firewall.."
           fw_stop
           log_end_msg $?
       ;;
       clean)
           log_daemon_msg "Clearing firewall rules.."
           fw_clear
           log_end_msg $?
       ;;
       status)
           log_daemon_msg "Firewall status"
           fw_status
       ;;
       *)
           log_action_msg "Usage $0 {start|stop|restart|clean|status}"
           exit 1
       ;;
   esac
   exit 0

```

On ubuntu I've got the following answer
```
~$ sudo insserv mon_parefeu
[sudo] Mot de passe de tinnitus : 
sudo: insserv : commande introuvable

```

The command cannot be found.
the insserv package is installed.

Can you help me?

---

### Post by wildmanne39 on 2018-05-31
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Freiklite on 2018-06-01
Hi,
The solution to the problem is:
```
$ service mon_parefeu start

long-lasting solution:
$ sudo update-rc.d mon_parefeu defaults

```
then vlc works.

Thanks
Bye.

---

