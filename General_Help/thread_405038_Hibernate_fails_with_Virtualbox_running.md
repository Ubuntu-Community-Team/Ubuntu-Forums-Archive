---
title: "Hibernate fails with Virtualbox running"
date: 2007-04-09
forum: General Help
---

### Post by eddiess on 2007-04-09
I have Ubuntu 7.04 running on my pc and normally the hibernate function works fine. But when I have Virtualbox running (with Windows XP) the hibernate function of Ubuntu doesn't work anymore. 

When I click 'hibernate' the screens goes black and it looks like the computer goes to hibernate, but it doesn't turn of. Instead of that it just goes back to my desktop.

Does anyone have a solution or tip for me to make this work?

---

### Post by cseljatib on 2007-09-10
hi there,
I do also have the same problem!!, nevertheless 'suspend' does work.
Also, I wanted to pointed out that virtualbox features are working properly!.

Did you got any answer or solution to this problem??, Did you post this in a different sub-forum??

PLEASE, let me know

---

### Post by webograph on 2008-03-25
to circumvent this, put this in ~/bin/vbox_suspend:
```
#!/bin/bash

for x in `vboxmanage -nologo list runningvms`
do
        vboxmanage -nologo controlvm $x savestate
done

```
and make it executable. you can test it by running ~/bin/vbox_suspend, which should save all your running virtual machines.

put the following lines in /etc/pm/sleep.d/90virtualbox and make it executable as well:
```

#!/bin/bash

case $1 in
        hibernate)
                su YOURUSER -c /home/YOURUSER/bin/vbox_suspend
                ;;
esac

```

this is not very elegant (as the user is hard-coded), but it works.
i have tried to make the machines resume on thaw, but it would place the vms on the wrong workspace even if it know which X server to use, which it doesn't.

---

