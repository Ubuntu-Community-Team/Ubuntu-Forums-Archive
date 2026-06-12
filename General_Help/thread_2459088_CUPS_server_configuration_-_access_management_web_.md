---
title: "CUPS server configuration - access management web interface"
date: 2021-03-10
forum: General Help
---

### Post by ilpdt08 on 2021-03-10
[COLOR=#242729][FONT=Arial]I am administering 100+ printers on my CUPS server (Ubuntu) located in 18 different departments. 
Therefore I would like to give certain users the ability to modify printers of their respective departments;[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
Department "km": 10 printers 1 printadmin "erik"[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
I have copied the default policy and edited it to reflect the department - like so;[/FONT][/COLOR]

```
 <Policy km>
  JobPrivateAccess default
  JobPrivateValues none
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

  ...

  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM erik
    Order deny,allow
  </Limit>
...

 </Policy>

```[COLOR=#242729][FONT=Arial]Every time I log in to the WebGUI with the user "erik" and try to modify a printer with the policy "km" assigned I'm getting the error;[/FONT][/COLOR][INDENT][FONT=inherit]Unable to modify printer: Forbidden[/FONT]
[/INDENT]
[COLOR=#242729][FONT=Arial]The Location segment in cupsd.conf looks like this;[/FONT][/COLOR]
```
<Location />
  Order allow,deny
  Allow all
</Location>

<Location /admin>
  AuthType Default
  Require valid-user
  Order allow,deny
  Allow all
</Location>

<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow all
</Location>

```[COLOR=#242729][FONT=Arial]
Thanks in advance! 

/Lars[/FONT][/COLOR]

---

