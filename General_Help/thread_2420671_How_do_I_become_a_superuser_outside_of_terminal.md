---
title: "How do I become a superuser outside of terminal?"
date: 2019-06-08
forum: General Help
---

### Post by shubanshii on 2019-06-08
When I try to connect to a server in pgAdminIII, get the following message: 

"Server instrumentation
The server lacks instrumentation functions. 
pgAdmin III uses some support functions that are not available by default in all PostgreSQL versions. These enable some tasks that make life easier when dealing with log files and configuration files. 
The adminpack is installed and activated by default if you are running the one-click installer of PostgreSQL. On Unix, you may have to install the contrib package, either with your package installer tool or by compilation. 
Once your extension is installed, you only need to click on the "Fix it!" button, so that pgAdmin installs this extension in your maintenance database."

The tutorials say to click the "Fix it button", but when I do so, it says I must be the superuser.  

Since this is not in the command prompt; how do I extend superuser privileges to the pgAdmin III GUI?

---

### Post by SeijiSensei on 2019-06-08
> On Unix, you may have to install the contrib package, either with your package installer tool or by compilation. 

Open a terminal and type

```
sudo apt install postgresql-contrib
```

---

