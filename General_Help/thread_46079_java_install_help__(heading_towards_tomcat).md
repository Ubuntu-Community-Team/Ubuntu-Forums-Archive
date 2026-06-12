---
title: "java install help  (heading towards tomcat)"
date: 2005-07-03
forum: General Help
---

### Post by cope on 2005-07-03
javac -version = javac 1.5.0_03

java -version  = 
java version "1.5.0_03"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_03-b07)
Java HotSpot(TM) Client VM (build 1.5.0_03-b07, mixed mode, sharing)

i have my basic java servlet saved as Hello.java

```
import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

public class Hello extends HttpServlet {

  public void doGet(HttpServletRequest req, HttpServletResponse res)
                               throws ServletException, IOException {

    res.setContentType("text/html");
    PrintWriter out = res.getWriter();

    String name = req.getParameter("name");
    out.println("<HTML>");
    out.println("<HEAD><TITLE>Hello, " + name + "</TITLE></HEAD>");
    out.println("<BODY>");
    out.println("Hello, " + name);
    out.println("</BODY></HTML>");
  }

  public String getServletInfo() {
    return "A servlet that knows the name of the person to whom it's" + 
           "saying hello";
  }
}

```


when i try to javac Hello.java it throws about 6-7 errors.
i'm not sure if its something i've installed, most likely the way its set up!

my errors are!

```

mark@dev:/var/www$ javac Hello.java
Hello.java:2: package javax.servlet does not exist
import javax.servlet.*;
^
Hello.java:3: package javax.servlet.http does not exist
import javax.servlet.http.*;
^
Hello.java:5: cannot find symbol
symbol: class HttpServlet
public class Hello extends HttpServlet {
                           ^
Hello.java:7: cannot find symbol
symbol  : class HttpServletRequest
location: class Hello
  public void doGet(HttpServletRequest req, HttpServletResponse res)
                    ^
Hello.java:7: cannot find symbol
symbol  : class HttpServletResponse
location: class Hello
  public void doGet(HttpServletRequest req, HttpServletResponse res)
                                            ^
Hello.java:8: cannot find symbol
symbol  : class ServletException
location: class Hello
                               throws ServletException, IOException {
                                      ^
6 errors


```

so its obviouslly not finding the java path.
can anyone give me a hand? i've been trying to fix this for a few days now, and i'm totally lost

---

### Post by adwait on 2005-07-03
[QUOTE=cope]javac -version = javac 1.5.0_03

java -version  = 
java version "1.5.0_03"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_03-b07)
Java HotSpot(TM) Client VM (build 1.5.0_03-b07, mixed mode, sharing)

i have my basic java servlet saved as Hello.java

```
import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

public class Hello extends HttpServlet {

  public void doGet(HttpServletRequest req, HttpServletResponse res)
                               throws ServletException, IOException {

    res.setContentType("text/html");
    PrintWriter out = res.getWriter();

    String name = req.getParameter("name");
    out.println("<HTML>");
    out.println("<HEAD><TITLE>Hello, " + name + "</TITLE></HEAD>");
    out.println("<BODY>");
    out.println("Hello, " + name);
    out.println("</BODY></HTML>");
  }

  public String getServletInfo() {
    return "A servlet that knows the name of the person to whom it's" + 
           "saying hello";
  }
}

```


when i try to javac Hello.java it throws about 6-7 errors.
i'm not sure if its something i've installed, most likely the way its set up!

my errors are!

```

mark@dev:/var/www$ javac Hello.java
Hello.java:2: package javax.servlet does not exist
import javax.servlet.*;
^
Hello.java:3: package javax.servlet.http does not exist
import javax.servlet.http.*;
^
Hello.java:5: cannot find symbol
symbol: class HttpServlet
public class Hello extends HttpServlet {
                           ^
Hello.java:7: cannot find symbol
symbol  : class HttpServletRequest
location: class Hello
  public void doGet(HttpServletRequest req, HttpServletResponse res)
                    ^
Hello.java:7: cannot find symbol
symbol  : class HttpServletResponse
location: class Hello
  public void doGet(HttpServletRequest req, HttpServletResponse res)
                                            ^
Hello.java:8: cannot find symbol
symbol  : class ServletException
location: class Hello
                               throws ServletException, IOException {
                                      ^
6 errors


```

so its obviouslly not finding the java path.
can anyone give me a hand? i've been trying to fix this for a few days now, and i'm totally lost[/QUOTE]
 JAVA_HOME=/usr/java/jre1.5.0_04
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH
 
Add these lines to /etc/bash.bashrc.

---

### Post by cope on 2005-07-03
```
 JAVA_HOME=/usr/java/jre1.5.0_04
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH

Add these lines to /etc/bash.bashrc.
```

i've added these lines (ammending the path to java/home)

/usr/lib/j2re1.5-sun
and it still doesn't work, even after a reboot. 
same 6 errors.

---

### Post by noodle on 2005-07-19
The package javax.servlet is not built into java. You need to point out to the java compiler where it can find the servlet jar file. This jar file comes with the tomcat web server.

---

