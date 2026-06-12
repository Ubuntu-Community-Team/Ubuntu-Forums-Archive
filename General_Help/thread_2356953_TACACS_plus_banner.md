---
title: "TACACS plus banner"
date: 2017-03-28
forum: General Help
---

### Post by antokapo on 2017-03-28
[COLOR=#000000]Hi [/COLOR]

[COLOR=#000000]I'm trying to set up banner display at login from cisco router using tacacs+ server on Ubuntu 14.04 .[/COLOR]

[COLOR=#000000]Every trila i've done was unsuccessful , at cisco router login i get always the default banner : [/COLOR]


[COLOR=#000000]"User Access Verification[/COLOR]

[COLOR=#000000]Username:[/COLOR]
[COLOR=#000000]"[/COLOR]

[COLOR=#000000]in my conf. file i have : [/COLOR]

[COLOR=#000000]################################################## #################[/COLOR]
[COLOR=#000000]# HOST AND SECRET[/COLOR]
[COLOR=#000000]################################################## #################[/COLOR]


[COLOR=#000000]#host = *.*.*.* {[/COLOR]
[COLOR=#000000]#type = cisco[/COLOR]
[COLOR=#000000]#prompt = "TACACS+ Login"[/COLOR]
[COLOR=#000000]#prompt = "Login ID: "[/COLOR]
[COLOR=#000000]#}[/COLOR]


[COLOR=#000000]host = *.*.*.* {[/COLOR]
[COLOR=#000000]# welcome banner = "\nTACACS+ Login\n"[/COLOR]
[COLOR=#000000]# prompt = "TACACS+ Login: "[/COLOR]
[COLOR=#000000]}[/COLOR]


[COLOR=#000000]( they're not working trials ... ) [/COLOR]

[COLOR=#000000]Have you any idea ? [/COLOR]


[COLOR=#000000]Thanks a lot [/COLOR]

[COLOR=#000000]Antonello[/COLOR]

[COLOR=#000000]TACACS plus running as : [/COLOR]

[COLOR=#000000]tac_plus version F4.0.4.26[/COLOR]
[COLOR=#000000]ACLS[/COLOR]
[COLOR=#000000]FIONBIO[/COLOR]
[COLOR=#000000]LIBWRAP[/COLOR]
[COLOR=#000000]LINUX[/COLOR]
[COLOR=#000000]LITTLE_ENDIAN[/COLOR]
[COLOR=#000000]LOG_DAEMON[/COLOR]
[COLOR=#000000]MAXSESS[/COLOR]
[COLOR=#000000]MAXSESS_FINGER[/COLOR]
[COLOR=#000000]PAM[/COLOR]
[COLOR=#000000]NO_PWAGE[/COLOR]
[COLOR=#000000]REAPCHILD[/COLOR]
[COLOR=#000000]RETSIGTYPE RETSIGTYPE[/COLOR]
[COLOR=#000000]SHADOW_PASSWORDS[/COLOR]
[COLOR=#000000]SIGTSTP[/COLOR]
[COLOR=#000000]SIGTTIN[/COLOR]
[COLOR=#000000]SIGTTOU[/COLOR]
[COLOR=#000000]SO_REUSEADDR[/COLOR]
[COLOR=#000000]STRERROR[/COLOR]
[COLOR=#000000]TAC_PLUS_PORT[/COLOR]
[COLOR=#000000]UENABLE[/COLOR]
[COLOR=#000000]__STDC__[/COLOR]

---

