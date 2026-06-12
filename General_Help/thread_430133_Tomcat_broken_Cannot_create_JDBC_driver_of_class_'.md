---
title: "Tomcat broken: Cannot create JDBC driver of class '' for connect URL 'null'"
date: 2007-05-01
forum: General Help
---

### Post by Jakara on 2007-05-01
Tomcat 5 and tomcat 5.5 on all three of my computers are always having problems, i always try to fix it for hours and then switch to a standard install from the tomcat website. Does anyone else have this problem. What the heck is the difference? Why does it cause so many problems to use the ubuntu install.

For example, at the moment I have simple web app that just opens a database connection and thats it. It works on a default install of tomcat, but not the ubuntu install (even with security manager turned off, and switching to java 1.5 and 1.6)

org.apache.commons.dbcp.SQLNestedException: Cannot create JDBC driver of class '' for connect URL 'null'

---

### Post by madmakis on 2008-01-31
We have exactly the same problem described above. The log shows the exception:

SQLException Cannot create PoolableConnectionFactory (Something unusual has occured to cause the driver to fail. Please report this exception.)

---

### Post by gholdys on 2008-05-02
Hi 

I've experienced both these problems on Ubuntu 7.10 with Tomcat 5.5. Fortunately, I have managed to solve them, so maybe my solutions will be helpful to someone.

The "Cannot create JDBC driver of class '' for connect URL 'null'" error was caused, in my case, by the fact, that the context.xml file that contained the definitions of JNDI resources (in my case, a local PostreSQL database) wasn't copied from META-INF folder of my application to the /usr/share/tomcat5.5/conf/Catalina/localhost where Tomcat seems to keep context files for deployed applications. After I symlinked the context.xml from my application to this folder and changed the link's name to aplicationName.xml everything started to work.

To the best of my knowledge the "Something unusual has occured..." exception can be caused by many different things. In my case, the problem was in policy files that are used by Tomcat. On Ubuntu these policy files are stored inside /etc/tomcat5.5/policy.d/ folder. In that folder, you should find a file called 04webapps.policy. This file contains security policies that apply to all web applications. Since I needed a connection to a database I had to add an entry, that grants applications the permission to access the database (which in my case was on the localhost, hence 127.0.0.1, listening on port number 32288). The entry looked like this:

grant {
     permission java.net.SocketPermission "127.0.0.1:32288", "connect,resolve,listen,accept";
};

And that was all.

I hope, my experiences can be of some use to someone.
Cheers.

---

