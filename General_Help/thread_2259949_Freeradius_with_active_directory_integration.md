---
title: "Freeradius with active directory integration"
date: 2015-01-08
forum: General Help
---

### Post by mrquainoo on 2015-01-08
Hi,
  I am pretty new to ubuntu and linux in general. I am trying to  intergrate Freeradius with Active Directory. I have successfuly  installed freeradius on ubuntu and i can run it in debug mode. I am then  trying to test the authentication with an AD user but i was getting the  error below:
  Error: Exec-Program: FAILED to execute /etc/freeradius/modules/ntlm_auth: Permission Denied.


  I therefore gave read and execute rights to the ntlm_auth file using the command below:
  setfacl -m u:freerad:rx ntlm_auth.


  and now i am getting another error, below:
  Error: Exec-Program: FAILED to execute /etc/freeradius/modules/ntlm_auth: Exec Format error


  Because of this error my authentication is failing since they generate different keys.
  Can someone help me solve this problem? or tell me where I am wrong :-)

---

### Post by mrquainoo on 2015-01-08
Hi,
  I am pretty new to ubuntu and linux in general. I am trying to  intergrate Freeradius with Active Directory. I have successfuly  installed freeradius on ubuntu and i can run it in debug mode. I am then  trying to test the authentication with an AD user but i was getting the  error below:
  Error: Exec-Program: FAILED to execute /etc/freeradius/modules/ntlm_auth: Permission Denied.


  I therefore gave read and execute rights to the ntlm_auth file using the command below:
  setfacl -m u:freerad:rx ntlm_auth.


  and now i am getting another error, below:
  Error: Exec-Program: FAILED to execute /etc/freeradius/modules/ntlm_auth: Exec Format error


  Because of this error my authentication is failing since they generate different keys.
  Can someone help me solve this problem? or tell me where I am wrong :-)

---

### Post by coffeecat on 2015-01-08
Threads merged.

---

