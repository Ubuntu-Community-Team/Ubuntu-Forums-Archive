---
title: "Online accounts through CLI"
date: 2023-12-12
forum: General Help
---

### Post by Jaxilian on 2023-12-12
Hi all,

I wonder how online accounts is created through the CLI. There must be an easy way or is it just if you pay the big bucks to Canonical? I don't want to click my way through them. I have an automated autoinstall image that needs this.
Both Microsoft Exchange and Enterprise Login (kerberos) for example.

---

### Post by TheFu on 2023-12-12
Online accounts for different services have different methods. Nothing prevents you from making a little script to the this, provided you have the skill and time.  Or you could pay someone else to make the script for you or, if Canonical offers a service that will connect a system to specific online accounts, it might be worth it to pay them.  IDK.

I'd never use MS-anything and avoid Google accounts as much as possible.  Your enterprise IT support team, if they are paying for only MS-Exchange access, might have access to enterprise documentation.

I have no idea what you mean by "Enterprise Login (kerberos)" - there has to be a backend authentication server, probably running some sort of identify management tool.  NDS, FreeIPA, or straight LDAP.  The logins would probably all be configured in PAM under Linux. That's how we did it at my company.  I suppose some companies might decide to use MS-AD for whatever reason, but that isn't what we did.

---

### Post by Jaxilian on 2023-12-13
> **TheFu said:**
> Online accounts for different services have different methods. Nothing prevents you from making a little script to the this, provided you have the skill and time.  Or you could pay someone else to make the script for you or, if Canonical offers a service that will connect a system to specific online accounts, it might be worth it to pay them.  IDK.

I'd never use MS-anything and avoid Google accounts as much as possible.  Your enterprise IT support team, if they are paying for only MS-Exchange access, might have access to enterprise documentation.

I have no idea what you mean by "Enterprise Login (kerberos)" - there has to be a backend authentication server, probably running some sort of identify management tool.  NDS, FreeIPA, or straight LDAP.  The logins would probably all be configured in PAM under Linux. That's how we did it at my company.  I suppose some companies might decide to use MS-AD for whatever reason, but that isn't what we did.

Both Microsoft Exchange and Enterprise Login (kerberos) are under online accounts. Online account Microsoft Exchange ties in good with Evolution so that works well, but I don't wanna configure it manually on each computer. There has to be good documentation on how to implement these automatically, maybe not with the online accounts but with scripts. I find nothing on how to fix it.

---

### Post by dragonfly41 on 2023-12-13
I face similar problems when in development I am faced with complex new web interfaces, even with shortcuts. I experiment with a multitude of services and apps mainly for my own development ideas. Every UI (CLI included) has to be remembered and often orchestrated together in pipelines.

And turning to YouTube tutorials you are faced with static screenshots which need to be laboriously extracted to replay to reproduce each  workflow. This led me into new territory of auto driving the service UI.

For example I recently started an Azure account and the choices of services are rather overwhelming (including Kerebos) for a new user.

I turn to using UI emulators which can "drive" each user interface by scanning the browser to look for either x,y targets or images.

So I use "orchestration" of UI with this helicopter view of different UI's. There are multiple tools for this uncommon approach. Here is one favourite on mine  .. [https://github.com/Jmgr/actiona](https://github.com/Jmgr/actiona)

In Ubuntu there is xdotool. Explore also pipedream.com for pipes.

In Python there is pyautogui.

For Java users there is Sikulix (reengineered Stanford project).

Returning to Actiona I prepare the targets as javascript vars (arrays) then I can create procedures. I prefer writing scripts in Sublime Text themn include the externally prepared file. Although you can write these in Actiona code editor (tiny fonts though).  Admittedy Actiona is more than 16 years old.

Don't forget also ansible scripts.  There is also Zapier to try to automate workflows.

One nice point about this approach is that you can write your workflows in Jupyter notebooks (in lieu of YouTube), part commentary, part code in multiple kernels.

For desktop terminal usage I use Yakuake.

But I admit that this approach is an "outlier" to usual practices of just learning each UI.
Azure, Heroku, Google, ... ... ...

---

