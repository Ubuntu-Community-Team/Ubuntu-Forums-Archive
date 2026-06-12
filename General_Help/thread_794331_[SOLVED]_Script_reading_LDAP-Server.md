---
title: "[SOLVED] Script reading LDAP-Server"
date: 2008-05-14
forum: General Help
---

### Post by borobudur on 2008-05-14
Can someone explain me how to write a script with reads from a LDAP server, an address book to check if a contact is its birthday? 

This script should run once a day and if there is a hit there should be a message.

I'm java programmer but I have never done anything on the Linux platform (well, some system programming long time ago).

Thanks for your input.

---

### Post by borobudur on 2008-05-19
*** bump ***

---

### Post by borobudur on 2008-05-23
Okay I wrote a program in Java. But how can I let it run once a day automatically?

---

### Post by stumac on 2008-05-23
You use the cron command from the command line to schedule execution of your program.

The syntax is in the man page.

---

### Post by borobudur on 2008-05-24
Thanks! I will do something like this:
```
crontab -e
```
Found [this]("http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/").

---

### Post by borobudur on 2008-05-26
A more convenient way is the [Gnome Alarm Clock]("http://alarm-clock.54.pl/"): nice user interface with an icon in the task panel.
This application would be something for the Ubuntu standard edition.

---

### Post by borobudur on 2008-05-26
If there is anyone interested in my little program, here is the result.

I have this command in a shell script:

**java -cp /path/to/birthday/home Birthday**

(of course you need to compile the java file, you need the runtime environment and you need to create the *keystore* with the *keytool* software if you have encrypted connection)

```
import java.awt.BorderLayout;
import java.awt.Button;
import java.awt.Color;
import java.awt.Frame;
import java.awt.Label;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.text.Format;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.Hashtable;

import javax.naming.Context;
import javax.naming.NamingEnumeration;
import javax.naming.NamingException;
import javax.naming.directory.DirContext;
import javax.naming.directory.InitialDirContext;
import javax.naming.directory.SearchControls;
import javax.naming.directory.SearchResult;


/*
 *  Calls the ldap server and checks if there is a contacts with its 
 *  birthday today.
 *  The result will be shown in a little window.
 *  
 *  @autor Stefan Wagner
 */
public class Birthday extends Frame implements ActionListener {

    /*
     *  Constructor sets the window visible.
     */
    public Birthday(String title, String msg) {
        super(title);
        setBackground(Color.lightGray);
        setLayout(new BorderLayout());
        setResizable(false);
        setLocation(100, 100);
        setSize(100, 100);
        add(new Label(msg), BorderLayout.CENTER);
        Button btn = new Button("OK");
        btn.addActionListener(this);
        add(btn, BorderLayout.SOUTH);
        pack();
        setVisible(true);
    }

    /**
     * Programs starting point.
     */
    public static void main(String[] args) {

        try {
           Hashtable env = new Hashtable();
           
           env.put(Context.INITIAL_CONTEXT_FACTORY, "com.sun.jndi.ldap.LdapCtxFactory");
           env.put(Context.PROVIDER_URL, "ldaps://subdomain.dyndns.org:636/");  
           env.put(Context.SECURITY_PRINCIPAL, "uid=user,ou=users,dc=subdomain,dc=dyndns,dc=org");  
           env.put(Context.SECURITY_CREDENTIALS, "passwd"); 
           env.put(Context.SECURITY_AUTHENTICATION, "simple");
           env.put(Context.SECURITY_PROTOCOL, "ssl");
           
           //THE LOCATION OF THE CACERTS MUST BE SPECIFIED
           java.security.Security.addProvider(new com.sun.net.ssl.internal.ssl.Provider());
           System.setProperty("javax.net.ssl.keyStore",  "keystore");
           System.setProperty("javax.net.ssl.trustStore","keystore");
           
           DirContext ctx = new InitialDirContext(env);
           SearchControls ctls = new SearchControls();
           NamingEnumeration answer = ctx.search("o=user,ou=addressbook,dc=subdomain,dc=dyndns,dc=org", "birthDate=" + getDateToday(), ctls);

           new Birthday("Birthday", formatResults(answer));
      
           // Close the context when we're done
           ctx.close();

         } catch(NamingException ne) {
           System.err.println(ne);
           ne.printStackTrace();
         } catch (Exception e) {
        e.printStackTrace();
         }

    }

    /*
     *  Action of the button: end programm.
     */
    public void actionPerformed(ActionEvent arg0) {
        setVisible(false);
        dispose();
    }

    /*
     *  Returns the date (without the year) from today in evolution format.
     */
    private static String getDateToday() {
           Format formatter = new SimpleDateFormat("*-MM-dd");
           return formatter.format(new Date());
    }

    /*
     *  Formats the answer from the server.
     */
    public static String formatResults(NamingEnumeration searchResult) throws Exception{
        String res = "";
            try {
                while (searchResult.hasMore()) {
                    SearchResult sr = (SearchResult)searchResult.next();
                    res += sr.getName() + "\n";
               }

            } catch (NamingException e) {
                e.printStackTrace();
            }
        
            if ("".equals(res)) {
                res = "Today is nobodys birthday.";
            }
            
        return res;
    }

}
```

---

