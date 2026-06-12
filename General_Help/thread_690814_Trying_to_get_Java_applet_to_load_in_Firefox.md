---
title: "Trying to get Java applet to load in Firefox"
date: 2008-02-07
forum: General Help
---

### Post by villindesign on 2008-02-07
I am trying to look at a webcam image embedded into a website using Firefox. I have Java installed and when I ran the code ```
~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default
[*], or type selection number: 2
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.

``` I selected option 2. I restarted firefox and the Java app did not load. When I type "about:plugins" in Firefox, I get this under the Java heading: ```
Java(TM) Plug-in 1.6.0_03-b05
 File name:  libjavaplugin_oji.so Java(TM) Plug-in 1.6.0_03   MIME Type Description Suffixes Enabled    application/x-java-vm Java 
Yes   application/x-java-applet Java 
Yes   application/x-java-applet;version=1.1 Java 
Yes   application/x-java-applet;version=1.1.1 Java 
Yes   application/x-java-applet;version=1.1.2 Java 
Yes   application/x-java-applet;version=1.1.3 Java 
Yes   application/x-java-applet;version=1.2 Java 
Yes   application/x-java-applet;version=1.2.1 Java 
Yes   application/x-java-applet;version=1.2.2 Java 
Yes   application/x-java-applet;version=1.3 Java 
Yes   application/x-java-applet;version=1.3.1 Java 
Yes   application/x-java-applet;version=1.4 Java 
Yes   application/x-java-applet;version=1.4.1 Java 
Yes   application/x-java-applet;version=1.4.2 Java 
Yes   application/x-java-applet;version=1.5 Java 
Yes   application/x-java-applet;version=1.6 Java 
Yes   application/x-java-applet;jpi-version=1.6.0_03 Java 
Yes   application/x-java-bean Java 
Yes   application/x-java-bean;version=1.1 Java 
Yes   application/x-java-bean;version=1.1.1 Java 
Yes   application/x-java-bean;version=1.1.2 Java 
Yes   application/x-java-bean;version=1.1.3 Java 
Yes   application/x-java-bean;version=1.2 Java 
Yes   application/x-java-bean;version=1.2.1 Java 
Yes   application/x-java-bean;version=1.2.2 Java 
Yes   application/x-java-bean;version=1.3 Java 
Yes   application/x-java-bean;version=1.3.1 Java 
Yes   application/x-java-bean;version=1.4 Java 
Yes   application/x-java-bean;version=1.4.1 Java 
Yes   application/x-java-bean;version=1.4.2 Java 
Yes   application/x-java-bean;version=1.5 Java 
Yes   application/x-java-bean;version=1.6 Java 
Yes   application/x-java-bean;jpi-version=1.6.0_03 Java 
Yes  
```This is the actual code in the webpage...
```
<OBJECT classid = "clsid:CAFEEFAC-0014-0001-0000-ABCDEFFEDCBA" codebase = "http://java.sun.com/products/plugin/autodl/jinstall-1_4_1-windows-i586.cab#Version=1,4,1,0" WIDTH = 640 HEIGHT = 500 >
             <PARAM NAME = CODE VALUE = "Device1.class" >
             <PARAM NAME = "type" VALUE = "application/x-java-applet;jpi-version=1.4.1"></OBJECT>
    </td>
```Does anyone know how I get the applet to load? Thanks

---

### Post by decodex on 2008-06-09
The problem with the <object> tag is... that you must implement twice... one for IE - browsers, the other for mozilla / Gecko Browsers...

the above mentioned code will only work on IE - Browsers...

i have made an applet implementation on ASP.net for both Browsers with asking for the type of Browser, the User is using...

Code:
> 
            <%
                Boolean isIE = false;
                if (Request.Browser.Browser.ToString() == "IE")
                {
                    isIE = true;
                }
            %>
            <%-- IF(!IE) ...(IF THE BROWSER IS NOT INTERNET EXPLODER!!! --%>
            <%
                if (!isIE)
                {
            %>
                    <object classid="java:Starter.class" type="application/x-java-applet" archive="http://..somearhive.../yourjarfilefolder/TEST.jar"
                        height="600px" width="100%">
                    </object>
            <%
                }
                else
                {
            %>
                    <object classid="clsid:CAFEEFAC-0014-0002-0000-ABCDEFFEDCBA" width="100%" height="600px"
                        codebase="http://java.sun.com/products/plugin/autodl/jinstall-1_4_2-windows-i586.cab#Version=1,4,2,0">
                        <param name="java_code" value="Starter.class" />
                        <param name="java_archive" value="http://..somearhive.../yourjarfilefolder/TEST.jar" />
                        <param name="java_codebase" value="html/" />
                        <param name="java_type" value="application/x-java-applet;jpi-version=1.4.2" />
                        <param name="scriptable" value="true" />
                    </object>
            <% 
                }
            %>


---

