---
title: "Tomcat MySQL and JDBC Connectivity"
date: 2007-12-23
forum: General Help
---

### Post by flossgeek on 2007-12-23
I am trying to set up an environment to run some java blog software. At current though I am just trying to get MySQL talking with Tomcat using the JDBC connector. I have tried to get this working for a week now, and still have no joy. Could anyone possibly push me in the right direction or see where I have gone wrong it would be really appreciated?

**Install Java Environment**

```
sudo apt-get install sun-java6-jdk sun-java6-plugin
```

```
sudo update-java-alternatives -s java-6-sun
```

Then opened /etc/jvm file:-

```
gksudo gedit /etc/jvm
```

Added the line 

```
/usr/lib/jvm/java-6-sun 
```

to the top of the entries.

**MySQL**

```
sudo apt-get install mysql-server
```

**Tomcat**

```
sudo apt-get install tomcat5.5 tomcat5.5-admin tomcat5.5-webapps
```

**Java database (JDBC) driver for MySQL **

```
sudo apt-get install libmysql-java
```

**Testing the connection**

To test the connection i am using the following code Connect.java:-

```

import java.sql.*;

   public class Connect
   {
       public static void main (String[] args)
       {
           Connection conn = null;

           try
           {
               String userName = "testuser";
               String password = "testpass";
               String url = "jdbc:mysql://localhost:3306/test";
               Class.forName ("com.mysql.jdbc.Driver").newInstance ();
               conn = DriverManager.getConnection (url, userName, password);
               System.out.println ("Database connection established");
           }
           catch (Exception e)
           {
               System.err.println ("Cannot connect to database server");
           }
           finally
           {
               if (conn != null)
               {
                   try
                   {
                       conn.close ();
                       System.out.println ("Database connection terminated");
                   }
                   catch (Exception e) { /* ignore close errors */ }
               }
           }
       }
   }

```

I create a new database called test and assign a user to the database with a username 'testuser' and a password 'testpass'.

```
mysql -u root -p
```

Create a database called 'test':

```
mysql> create database test;
```

Create a user named 'testuser' with a password 'testpass'.

```

mysql> grant all on test.* to 'testuser'@'localhost' identified by 'testpass';
mysql> use test;
mysql> flush privileges;
mysql> \q

```

**Compiled Connect.java**

```
javac Connect.java
```

then ran the class file

```
java Connect
```

*The program does not connect due to an exception. And shows the **Cannot connect to database server to the output. What is wrong here, help would be appreciated. Thanks ...***

---

### Post by thelinuxguy on 2007-12-23
If you did an e.printStackTrace() in the catch block or just threw the exception, that would tell some more about where the problem really is. Could you post the stack trace?

---

### Post by flossgeek on 2007-12-23
I added the e.printStackTrace() to the catch:-

heres the output:

java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at Connect.main(Connect.java:14)

Cheers

---

### Post by thelinuxguy on 2007-12-23
Seems like the driver jar is not in the classpath. Put the following files in your classpath. I am not sure if both are required. Try putting either and then both.
```

/usr/share/java/mysql-connector-java-5.0.4.jar
/usr/share/java/mysql-connector-java.jar

```

```

java -cp "/usr/share/java/mysql-connector-java-5.0.4.jar":"/usr/share/java/mysql-connector-java.jar":. Connect

```

---

### Post by flossgeek on 2007-12-23
Thank you! I have progress, looks like it was a classpath issue. Basically I added the following to the .bashrc file located in the home directory.

```

export CLASSPATH=$CLASSPATH:/usr/share/java/mysql-connector-java-5.0.4.jar

```

---

### Post by flossgeek on 2007-12-23
Would it be possible you could email me at [email]leetambiah@ossgeeks.co.uk[/email]....

---

