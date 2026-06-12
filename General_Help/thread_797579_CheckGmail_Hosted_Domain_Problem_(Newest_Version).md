---
title: "CheckGmail Hosted Domain Problem (Newest Version)"
date: 2008-05-17
forum: General Help
---

### Post by lembregtse on 2008-05-17
Since yesterday morning ( Friday 16-May-2008 ) my CheckGmail can't get logged into my hosted google domain account.

It keeps returning the fact that I entered the wrong user credentials!
But everything has been running smoothly for over months, and I'm using the latest svn version!

Now I was wondering if I'm the only one with this problem or not?

Because it seems that the interface also has changed (of Google Mail)
So they might have changed the API or something like that I guess, but just was wondering if there are other people arround there with this problem!

Kind Regards,
Eric Lembregts

[b]
Edit:

I think I've found a solution for this problem, but as I don't know how to bring something out to fix it I'll post it right here.
You need to edit /usr/bin/checkgmail

And replace line 730 with this:
[/b]
```
$error = http_get("https://www.google.com/a/$hosted/LoginAction2|at=null&continue=http%3A%2F%2Fmail.google.com%2Fa%2F$hosted&service=mail&Email=$URI_user&Passwd=$URI_passwd", "POST");
```
[b]
Things they changed:
- LoginAction2 instead of LoginAction
- Email instead of userName
- Passwd instead of password

Then start checkgmail and normally it should work, it seems that google changed there API for Hosted Gmail!

I don't know if there are some other changes but for now it seems to work here, if any problems found please report here!

I hope this works!
[/b]

---

### Post by fakeollie on 2008-05-18
You're definitely not the only one, Eric. I can confirm the same exact behaviour on my checkgmail and it started a few days ago like yours. I also use it to check google mail for a hosted domain.

No solutions so far, the checkgmail page still have no information about it and it hasn't been updated in a while: [http://checkgmail.sourceforge.net](http://checkgmail.sourceforge.net)

---

### Post by lembregtse on 2008-05-18
[Topic Post Edit]: Added temporary solution!

---

### Post by jester2.0 on 2008-05-25
This solution worked perfectly for me.  Thank you much!!

---

### Post by ctothej on 2009-01-10
That solution worked for me too. Thank you.

---

### Post by HuckBerry on 2009-08-22
I hate to reawaken an old thread, but I seem to still be having issues. 
checkgmail has updated recently to include the fix mentioned above and as of the most recent version that line is on 782
I'm attempting to use a hosted domain by using this example code:

```

checkgmail -profile=alternateprofilename -hosted=studentserver.college.edu -v

```which returns:
```

CheckGmail v1.13svn
Copyright Â© 2005-7 Owen Marshall

Initialisation complete
Logging in to Gmail ...
Saved cookie: JSESSIONID
DE27896ED5306F136D73BF5CD5E5E548

Saved cookie: JSESSIONID
DE27896ED5306F136D73BF5CD5E5E548

Error: 401 Unauthorised

```Any suggestions?

---

### Post by espurious on 2009-08-27
401 Unauthorised Fix

Gmail recently changed the login procedure, resulting in this error. To fix this issue, please use the latest version from SVN -- the easiest way to do this is to run checkgmail -update from the commandline and follow the prompts.

From [http://checkgmail.sourceforge.net/](http://checkgmail.sourceforge.net/)

---

### Post by HuckBerry on 2009-08-27
Careful observation of my code output shows I am already using 1.13svn (most recent version I know of). I even mentioned that update in my original post. Does anyone have any useful information about the login procedure for hosted gmail domains?

I have stated editing the script myself and interpreting the cookie trail left by logging in manually but I can't seem to get to the gmail HID and GMAIL_AT cookies.

current code:
```

unless ($hosted) {
                # Normal Gmail login action ...
                $error = http_get("https://www.google.com/accounts/ServiceLoginAuth?ltmpl=yj_wsad&ltmplcache=2&continue=https%3A%2F%2Fmail.google.com%2Fmail%3F&service=mail&rm=false&ltmpl=yj_wsad&Email=$URI_user&Passwd=$URI_passwd&rmShown=1&null=Sign+in", "LOGIN");

                $cookie_jar->scan(\&scan_at);
                unless ($error || !$gmail_sid || !$gmail_gausr) {
                    $error = http_get("https://mail.google.com/mail/?pli=1&auth=$gmail_sid&gausr=$gmail_gausr", 'LOGIN');
                }

                # $error = http_get("https://mail.google.com/mail?nsr=0&auth=$gmail_sid&gausr=$gmail_gausr", "LOGIN");
    
            } else {
##BOOKMARK1
                     ##$error = http_get("https://www.google.com/a/$hosted/LoginAction2|at=null&continue=http%3A%2F%2Fmail.google.com%2Fa%2F$hosted&service=mail&Email=$URI_user&Passwd=$URI_passwd", "POST");

                $error = http_get("http://northampton.edu", "GET");
                $error = http_get("http://www.northampton.edu/x638.xml.", "GET");
                $error = http_get("https://carsweb.northampton.edu/cgi-bin/student/frame.cgi", "GET");
                print "   GET a remote user cookie from shib\n";

                print "    Cookies:    (SHOULD HAVE SHIB)\n";
                $cookie_jar->scan(\&scan_at);

                $error = http_get("https://shib.northampton.edu/idp/Authn/j_security_check|j_username=XXXXXX&j_password=XXXXXX", "POST2");
                print "   GET a login to idp\n";

                $error = http_get("https://carsweb.northampton.edu/Shibboleth.sso/SAML2/POST", "GET"); 


                print "    Cookies:    (SHOULD HAVE IDP)\n";
                $cookie_jar->scan(\&scan_at);

                $error = http_get("http://mail.google.com/a/spartan.northampton.edu/?account_id=mberry%40spartan.northampton.edu&AuthEventSource=SSO", "GET");
                print "   GET a HID from hosted mail\n";

                print "    Cookies:    (SHOULD HAVE HID)\n";
                $cookie_jar->scan(\&scan_at);


                # And now we login with that cookie, which will give us the GMAIL_AT cookie!
                unless ($error || !$gmail_hid) {
                    $error = http_get("https://mail.google.com/a/spartan.northampton.edu?AuthEventSource=Internal&auth=$gmail_hid", 'GET');    
                    print "    GETED a GMAIL_AT from hosted mail\n";        
                }
            }

            $cookie_jar->scan(\&scan_at);
            
            unless ($gmail_at) {
                print "   HOSTED mail login cookie missing\n";
                unless ($error) {
                    print "    However Connection  is present\n";
                    $http_status->enqueue("Error: 401 Unauthorised");
                    $error_block->down;
                } else {
                    print "    NO connection Error\n";
                    # simple block to prevent checkgmail hogging CPU if not connected!
                    sleep 30;
                }
                
                redo;
            }
        }

        print "Logged in ... AT = $gmail_at\n" unless $silent;
    }        

```There's more code I edited, but that is the important part.

~Matt

---

### Post by computercolin on 2010-03-15
#huckberry, any further luck. I'm also following the cookie trail but not able to get ahold of the GMAIL_AT cookie.

---

### Post by HuckBerry on 2010-03-15
Yes I did get a little bit further, if you check out this link 

[http://code.google.com/googleapps/domain/sso/saml_reference_implementation.html](http://code.google.com/googleapps/domain/sso/saml_reference_implementation.html)

and follow the flowchart to step 6, the SAML server sends it's response to the user's browser in the form of a self-submitting <FORM> where the form action points at Google's server. The problem is that PERL will not execute the javascript to submit that form.

My knowledge of PERL is limited, I attempted to parse out the SAML strings and post them myself to google's servers, but the connection would always reset when I attempted it.

Hopefully this info is what you were looking for, not all hosted domains use SSO, but for those that do, this is the procedure.

~Huckle

---

### Post by rexmilton on 2010-09-07
how can I get CheckGmail to print out my PDF attachments when they arrive?

---

### Post by TabletUbuntu on 2010-09-12
Using the latest CheckGmail v1.14pre-svn.  Still have the error 401 unauthorised login.  Can anyone confirm this is still an issue with the latest version?

---

### Post by astrobob.tk on 2010-09-21
Hey guys,

I am having a problem with checkgmail: its simply not working. I click the icon & nothing happens. I even added it to the startup applications & still nothing happens. Its not working.

Could you please help ?

thx

---

