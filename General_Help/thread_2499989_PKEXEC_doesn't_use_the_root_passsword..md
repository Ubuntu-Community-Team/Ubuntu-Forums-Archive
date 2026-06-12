---
title: "PKEXEC doesn't use the root passsword."
date: 2024-08-17
forum: General Help
---

### Post by luca-dgh on 2024-08-17
Hi!
I use Ubuntu 24.04 with Mate desktop. On my pc I have only 1 account, but all my family occasionally accesses the pc (printing, scanning or whatever other need). For many reasons I don't want to manage more accounts or GUEST account. So I set my account with a medium strong easy to remember password, but I put a very strong password to root (in order to protect admin tasks) and in sudoers I added the line ```
Defaults   targetpw
```Up to 22.04 that was enough to grant that my account password could not start admin tasks.
Now, in 24.04 I can see that many admin tasks start from menu with my medium strong password (root password doesn't start them), after many tries I understand that PKEXEC is the responsible, because if I start them with SUDO they works only under the root password, if I start them with PKEXEC the task works only with my personal password.
So, is it a bug or is a feature?
Is there a fix to this?
Thx in advance for your help.

---

### Post by luca-dgh on 2024-08-17
Ok, I was forgetting one step. Some years ago, in 2016, I reported [a bug for the same reason ]("https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/1643931")and they told me how to modify policykit files. However that solution is not working for 24.04, the policykit folder is empty now, I tried putting there the file that was working on 22.04, but it doesn't work.
I suppose they changed something in poilicykit, can someone helps me?

---

### Post by luca-dgh on 2024-08-23
Ok, in Arch Wiki I found the solution


 in /etc/polkit-1/rules.d/49-rootpw_global.rules  I create the rule


 /* Always authenticate Admins by prompting for the root
 * password, similar to the rootpw option in sudo
 */
polkit.addAdminRule(function(action, subject) {
    return ["unix-user:root"];
});


 Now PKEXEC works only with root password.

---

