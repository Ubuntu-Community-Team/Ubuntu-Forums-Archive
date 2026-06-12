---
title: "Updated firefox Version: 1.0.2-0ubuntu5.3 won't start"
date: 2005-05-26
forum: General Help
---

### Post by rotorwash on 2005-05-26
The update manager updated firefox to the version in the title. Now upon startup the following message appears:

INTERNAL ERROR on Browser End: JavaPluginFactory5 init - no agent?

System error?:: No such file or directory

Can someone point me in the right direction for troubleshooting this problem?

---

### Post by cutOff on 2005-05-26
[QUOTE=rotorwash]The update manager updated firefox to the version in the title. Now upon startup the following message appears:

INTERNAL ERROR on Browser End: JavaPluginFactory5 init - no agent?

System error?:: No such file or directory

Can someone point me in the right direction for troubleshooting this problem?[/QUOTE]
I don't know how you have installed java on Ubuntu but you can try to do it as says [here](http://ubuntuguide.org/#jre).

---

### Post by rotorwash on 2005-05-26
[QUOTE=cutOff]I don't know how you have installed java on Ubuntu but you can try to do it as says [here](http://ubuntuguide.org/#jre).[/QUOTE]

Thanks. That pointed me in the right direction... I forgot about the plugin. Since I do java dev on this machine I have multiple versions of the java sdk and jre. The plugin was causing firefox to fail on startup although the previous version functioned fine. I will figure out what has changed in the version and fix my environment.

---

