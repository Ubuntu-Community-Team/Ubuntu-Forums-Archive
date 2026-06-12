---
title: "How to allow PUT HTTP method"
date: 2017-09-28
forum: General Help
---

### Post by therrle on 2017-09-28
Hi there,
can anyone tell me how to enable the PUT HTTP method globally in Aopache 2.4 on Ubuntu 16.04?
I already tried several things but none work. I have a Reverse proxy config for Jira. In short it looks like this:

<VirtualHost *:443>
       SSLEngine on


        # JIRA Proxy Configuration:
        <Proxy *>
                Order deny,allow
                Allow from all
                AllowMethods GET POST PUT DELETE OPTIONS
        </Proxy>
        SSLProxyEngine          On
        ProxyRequests           Off
        ProxyPreserveHost       On
        ProxyPass               /       [http://localhost:8080/](http://localhost:8080/)
        ProxyPassReverse        /       [http://localhost:8080/](http://localhost:8080/)
</VirtualHost>





My 1st approach was with limit inside my Proxy * config:

                <Limit GET POST PUT DELETE OPTIONS>
                        Require all granted
                </Limit> 

after that I tried
        <RequireAny>
        Require method DELETE GET POST PUT OPTIONS
        </RequireAny>

lastly I tried 

AllowMethods GET POST PUT DELETE OPTIONS

I always did 
apachectl configtest
apachectl restart

Nothing works. Whenever I do a PUT Request via curl it shows

curl -H "Content-Type: application/json" -X PUT -d '{"comment": "I did some work here.","visibility": {"type": "group","value": "jira-developers"},"started": "2017-09-27T13:06:14.160+0000","timeSpentSeconds": 12000}' https:/hostname/rest/api/2/issue/blubb/worklog -vvvv

---

