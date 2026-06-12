---
title: "Third party software (SAS) doesn't run in Edgy"
date: 2006-12-16
forum: General Help
---

### Post by useResa on 2006-12-16
[COLOR=Navy][I]Let me start by stating that I could not really find an appropriate section to post this thread in, therefor I have placed it here in General Help.
If there is a more appropriate section, please move this thread there.[/I][/COLOR]

The company I work for is a dedicated partner of [SAS Institute]("http://www,sas,com") in the Netherlands.
Their software also runs on Linux and I had their software running in Ubuntu Dapper. 
However, after the upgrade to Edgy their software did not work anymore.

Since I did not a clean install of Edgy but an upgrade, I thought this could be the cause and therefor I have re-installed the SAS software entirely. 
Unfortunately still with the same result, it does not run at all. 
I have also Feisty running in a VM, but also in Feisty the SAS software does not run anymore.

What sort of surprised me is the following. My understanding is that Ubuntu is based on Debian. 
In another VM I have Debian Etch RC1 running and the SAS software runs without any problems on Debian.

What I would like to know is the following:[LIST]
[*]Can anyone help me solve this issue? I would like to remain using Ubuntu, but if the main software for doing my job doesn't work in Ubuntu I have a serious problem.
[*]What sort of information can and/or should I provide in order to help you indicate the cause?[/LIST]I really hope someone can help me out here.

---

### Post by juraj on 2006-12-16
There can be a billion of reasons why your software doesn't work. Can you please say what exactly doesn't work?

---

### Post by useResa on 2006-12-16
> **juraj said:**
> There can be a billion of reasons why your software doesn't work. Can you please say what exactly doesn't work?
I can not even start it! 

I don't know if it is any help, but please find below the log from the software itself. Maybe this will give you a clue.
> Stack overflow detected In Task ( EVENTTSK ]
Fault and traceback information not available
Task Traceback

FATAL ERROR: WRCODE=80000803, MODULE='vtinit': Cannot Create event task

Traceback
No Traceback Available

Stack overflow detected In Task ( sasxkern ]
Fault and traceback information not available
Task Traceback

Stack overflow detected In Task ( EVENTTSK ]
Fault and traceback information not available

---

