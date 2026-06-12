---
title: "Mailserver setup"
date: 2007-01-11
forum: General Help
---

### Post by stepheny on 2007-01-11
Hello,

I am trying to set up a mailserver  which will retrieve my emails from the ISP and then distribute them locally according to the name in the To: header. My ISP allows me to use several "aliases" therefore mail for me has [email]stephen.smith@ISP.com[/email] and mail for my wife has [email]barbara.smith@ISP.com[/email] in the To: header even though my account is [email]fred.smith@ISP.com[/email]. 

With Fetchmail I can retrieve all of the mails for [email]fred.smith@ISP.com[/email] but how do I then seperate mail for stephen.smith and barbara.smith?

I am using Postfix as an MDA and can send my mail via my LAN from either computer/name with no problem, but if I need to change Postfix for another MDA to solve this distribution problem, I am prepared to do that. It is just that I have seen so many combinations offered as a solution to this (Fetchmail with multidrop, Postfix and Dovecot, gmail,etc.) and none of them has achieved what I need to do, even though I feel sure that it must be a fairly common requirement.

Thanks in advance.

---

### Post by stepheny on 2007-01-15
To clarify the aim of this project, I was trying to set up a mailserver which will retrieve my emails from the ISP and then distribute them locally according to the name in the To: header. My ISP allows me to use several “aliases” therefore mail for me has [email]stephen.smith@ISP.com[/email] and mail for my wife has [email]barbara.smith@ISP.com[/email] in the To: header even though my account is [email]fred.smith@ISP.com[/email]. This little project turned out to be very difficult because the configuration information for the various components was scattered about and there is also a lot of wrong configuration info out there. After a few days googling I managed to get the server to filter Barbara’s emails and put them in a directory that was reachable by her Outlook client.

I used Postfix, Fetchmail, Procmail and Dovecot to make this work.

**Postfix:** This was the easiest part, I installed Postfix, added the line home_mailbox = Maildir/ in /etc/postfix/main.cf to make postfix use Maildir as opposed to Mbox and added the LAN address to “mydestination” and it just worked. Here is my Postfix config file.

# appending .domain is the MUA's job.
append_dot_mydomain = no
# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = localhost.localdomain, localhost
relayhost = smtp.isp.com
mynetworks = 127.0.0.0/8, 192.168.0.0/24
mailbox_command = procmail -a “$EXTENSION”
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
inet_protocols = all

**Fetchmail:** I added lines to .fetchmailrc make fetchmail send its output to Procmail. The .fetchmailrc resides in my $HOME directory, here is a copy.

server pop.isp.com
proto pop3
user fred.smith
password nottelling
mda ‘procmail -f-’
mda “/usr/bin/procmail -d %s” # tell fetchmail which MDA to use

**Procmail:** The .procmailrc file also lives in my $HOME directory. There are two important points here:
1) don’t forget the trailing “/” in the directory names as it informs Procmail to use Maildir format.
2) The UMASK=007 is essential in order to make the moved mails readable by the group. Procmail automatically makes the owner the user using Procmail and sets the permission to owner only! The .procmailrc is here.

UMASK=007
PATH=/usr/bin:/usr/local/bin
MAILDIR=$HOME/Maildir/
DEFAULT=$HOME/Maildir/steve/
LOGFILE=$HOME/procmail.log
SHELL=/bin/sh
# Put mail for barbara into mailbox barbara
:0:
* ^To:.*barbara.smith
/home/barbara/Maildir/barbara/

**Dovecot:** There is some good information at the Dovecot WiKi [http://wiki.dovecot.org/](http://wiki.dovecot.org/) but unfortunately it is hard to find as the site seems more interested in showing you how to use a Wiki than making it easy to navigate through the Dovecot information. In the Dovecot configuration file /etc/dovecot/dovecot.conf make sure that:
1) listen = * or the IP address of your LAN, ie “listen = 192.168.0.0/24, localhost”.
2) ssl_disable = yes at least for the setup phase. I intend to set up ssl etc now that I have everything working but getting it working was my first priority. Here is the confiuration file

protocols = pop3 pop3s
listen = *
ssl_disable = yes
disable_plaintext_auth = no
log_timestamp = “%Y-%m-%d %H:%M:%S “
mail_extra_groups = steve
default_mail_env = maildir:/home/%u/Maildir/%u
protocol pop3 {
login_executable = /usr/lib/dovecot/pop3-login
mail_executable = /usr/lib/dovecot/pop3
pop3_enable_last = no
pop3_uidl_format = %08Xu%08Xv
}
auth default {
mechanisms = plain
passdb pam {
}
userdb passwd {
}
user = root
}
plugin {
}

Now it’s working but I will have to study the SSL features to make it really safe.

---

