---
title: "Ubantu 22.04 fail2ban not sending email notification on failed login attempt"
date: 2022-12-26
forum: General Help
---

### Post by leocap on 2022-12-26
[SIZE=5][COLOR=#232629][FONT=-apple-system]I setup smtp on my ubantu server and also successfully sent test mail.[/FONT][/COLOR]
[/SIZE][SIZE=4][COLOR=#232629][FONT=-apple-system]echo "This is the body of the email" | mail -s "This is the subject line" my_email_address[/FONT][/COLOR][/SIZE]
[COLOR=#232629][FONT=-apple-system][[IMG]https://i.stack.imgur.com/xTflu.png[/IMG]]("https://i.stack.imgur.com/xTflu.png")[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]
[SIZE=5]I am using fail2ban for getting email notification for failed login. But I am not understanding why I am not receiving any email notification? faile2ban blocking the ip but why it's not sending the email notification ? here is my jail.local file:[/SIZE][/FONT][/COLOR]

sender = my_server_address
mta = sendmail
destemail = tar***@gmail.com
mta = sendmail
protocol = tcp
port = [COLOR=var(--highlight-namespace)][FONT=inherit]0[/FONT][/COLOR]:[COLOR=var(--highlight-namespace)][FONT=inherit]65535[/FONT][/COLOR]
fail2ban_agent = Fail2Ban/%(fail2ban_version)s
action_ = %(banaction)s[port=[COLOR=var(--highlight-variable)][FONT=inherit]"%(port)s"[/FONT][/COLOR], protocol=[COLOR=var(--highlight-variable)][FONT=inherit]"%(protocol)s"[/FONT][/COLOR], chain=[COLOR=var(--highlight-variable)][FONT=inherit]"%(chain)s"[/FONT][/COLOR]]
action_mw = %(action_)s
            %(mta)s-whois[sender=[COLOR=var(--highlight-variable)][FONT=inherit]"%(sender)s"[/FONT][/COLOR], dest=[COLOR=var(--highlight-variable)][FONT=inherit]"%(destemail)s"[/FONT][/COLOR], protocol=[COLOR=var(--highlight-variable)][FONT=inherit]"%(protocol)s"[/FONT][/COLOR], chain=[COLOR=var(--highlight-variable)][FONT=inherit]"%(chain)s"[/FONT][/COLOR]]
action_mwl = %(action_)s
             %(mta)s-whois-lines[sender=[COLOR=var(--highlight-variable)][FONT=inherit]"%(sender)s"[/FONT][/COLOR], dest=[COLOR=var(--highlight-variable)][FONT=inherit]"%(destemail)s"[/FONT][/COLOR], logpath=[COLOR=var(--highlight-variable)][FONT=inherit]"%(logpath)s"[/FONT][/COLOR], chain=[COLOR=var(--highlight-variable)][FONT=inherit]"%(chain)s"[/FONT][/COLOR]]

[sshd]
enabled = true
port    = ssh
logpath = %(sshd_log)s
backend = %(sshd_backend)s

---

