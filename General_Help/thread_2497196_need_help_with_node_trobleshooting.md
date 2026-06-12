---
title: "need help with node trobleshooting"
date: 2024-04-26
forum: General Help
---

### Post by shan2edward on 2024-04-26
Hi ,
i'm developing a mysql, node, angular, express project.
the problem is everytime i create a new API it is giving 404 error in postman.
i use xampp for mysql for the stack im developing. Any troubleshooting steps are welcomed as im new to ubuntu.
Regards,
Gowri Shankar

---

### Post by dragonfly41 on 2024-04-26
I'm going through node/npm upgrade right now. So we can sync. Run these.

node --version


npm --version

---

### Post by shan2edward on 2024-04-26
kuber@kuber:~/sidgptproject/sidgptangular/backend$ node --version
v18.20.1
kuber@kuber:~/sidgptproject/sidgptangular/backend$ npm --version
10.5.0
kuber@kuber:~/sidgptproject/sidgptangular/backend$

---

### Post by shan2edward on 2024-04-26
> **dragonfly41 said:**
> I'm going through node/npm upgrade right now. So we can sync. Run these.

node --version


npm --version

[COLOR=#000000]kuber@kuber:~/sidgptproject/sidgptangular/backend$ node --version[/COLOR]
[COLOR=#000000]v18.20.1[/COLOR]
[COLOR=#000000]kuber@kuber:~/sidgptproject/sidgptangular/backend$ npm --version[/COLOR]
[COLOR=#000000]10.5.0[/COLOR]
[COLOR=#000000]kuber@kuber:~/sidgptproject/sidgptangular/backend$[/COLOR]

---

### Post by dragonfly41 on 2024-04-26
I have v 18.0.0 and am going through upgrade process to 20 required by an app (different from yours).
Encountered errors, and following advice ran:
which -a node
found  had two versions of node installed.
/usr/bin/node
/bin/node


Next step to clear out and reinstall node.

---

### Post by shan2edward on 2024-04-26
> **dragonfly41 said:**
> I have v 18.0.0 and am going through upgrade process to 20 required by an app (different from yours).
Encountered errors, and following advice ran:
which -a node
found  had two versions of node installed.
/usr/bin/node
/bin/node


Next step to clear out and reinstall node.

but i found only one installation

kuber@kuber:~/sidgptproject/sidgptangular/backend$ which -a node
/home/kuber/.nvm/versions/node/v18.20.1/bin/node
kuber@kuber:~/sidgptproject/sidgptangular/backend$

---

### Post by #&amp;thj^% on 2024-04-26
Just driving by but I also see what you found dragonfly41
```
which -a node
/usr/bin/node
/bin/node

```
```
node --version
v18.19.1

```

Apologies for any confusion

---

### Post by Holger_Gehrke on 2024-04-26
It's not a problem, it's the exact same file since /bin/ is a symlink to /usr/bin these days.

Holger

---

### Post by dragonfly41 on 2024-04-26
The issue I have is bumping up to v 20.

Errors were encountered while processing:
 /var/cache/apt/archives/nodejs_20.12.2-1nodesource1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dragonfly41 on 2024-04-26
Switching to OP's parallel issues (lest I be accused of highjacking) here is what my Sherlock Holmes agent comes up with:

[COLOR=#1B1642][FONT=&amp][FONT=var(--bs-font-monospace) !important][PROMPT] Concurrent with this session another party reports: i'm developing a mysql, node, angular, express project.the problem is everytime i create a new AP...[/FONT][/FONT][/COLOR]

[COLOR=#1B1642][FONT=&amp]**ANSWER | PHIND-70B MODEL**


When developing a MySQL, Node, Angular, Express project and encountering a 404 error for new APIs in Postman, there are several areas to investigate and potential solutions to apply. This issue typically arises from misconfigurations in the Express server setup, incorrect API endpoint definitions, or issues with the server's routing. Here's a parallel approach to troubleshoot and resolve the issue:

**1. Check API Endpoint Definitions**


Ensure that the API endpoints you're trying to access are correctly defined in your Express application. This includes verifying the HTTP method (GET, POST, PUT, DELETE, etc.) and the route path. A common mistake is a typo in the route path or using the wrong HTTP method.

**2. Verify Express Server Configuration**



[LIST]
[*]Middleware Configuration: Ensure that your Express server is correctly configured to use middleware for parsing JSON payloads (express.json()) and handling CORS if your API is being accessed from a different origin. This is crucial for APIs that will be consumed by a frontend application like Angular [4]("https://dev.to/juliest88/how-to-build-rest-api-with-nodejs-express-and-mysql-31jk").
[/LIST]


[LIST]
[*]Error Handling Middleware: Implement or verify the presence of error handling middleware in your Express application. This middleware should catch any requests to undefined routes and return a 404 error with a custom message, such as "Endpoint Not Found" [4]("https://dev.to/juliest88/how-to-build-rest-api-with-nodejs-express-and-mysql-31jk").
[/LIST]

**3. Review Express Routes**



[LIST]
[*]Route Definitions: Double-check your route definitions in Express to ensure they match the endpoints you're trying to access. This includes the correct use of app.get(), app.post(), etc., and the correct path specified [4]("https://dev.to/juliest88/how-to-build-rest-api-with-nodejs-express-and-mysql-31jk").
[/LIST]


[LIST]
[*]Route Order: The order in which routes are defined in Express matters. Ensure that your catch-all 404 middleware is placed after all your API route definitions. If it's placed before, it might catch requests to valid routes, leading to false 404 errors [4]("https://dev.to/juliest88/how-to-build-rest-api-with-nodejs-express-and-mysql-31jk").
[/LIST]

**4. Check for Typos**



[LIST]
[*]Endpoint Paths: A common cause of 404 errors is a simple typo in the endpoint path. Double-check the paths you're using in Postman against those defined in your Express application.
[/LIST]


[LIST]
[*]HTTP Methods: Ensure that you're using the correct HTTP method (GET, POST, etc.) in Postman that matches the method defined in your Express route.
[/LIST]

**5. Server Running and Port**



[LIST]
[*]Server Status: Ensure that your Express server is running. You can check this by looking at the console output when you start your server.
[/LIST]


[LIST]
[*]Port Configuration: Verify that the port your Express server is listening on matches the port you're using in Postman. If you're using environment variables to configure the port, ensure that the .env file is correctly set up and loaded into your application [4]("https://dev.to/juliest88/how-to-build-rest-api-with-nodejs-express-and-mysql-31jk").
[/LIST]

**6. CORS Configuration**


If your Angular application is served from a different origin (domain, protocol, or port) than your Express API, ensure that you have correctly configured CORS in your Express application. This is crucial for allowing your Angular application to make requests to your Express API [4]("https://dev.to/juliest88/how-to-build-rest-api-with-nodejs-express-and-mysql-31jk").

**7. Debugging**



[LIST]
[*]Logging: Add console logs in your Express route handlers to ensure that the requests are reaching your server and to help identify where the request might be failing.
[/LIST]


[LIST]
[*]Postman Console: Use the Postman console to inspect the details of the request and response. This can provide clues about what might be going wrong.
[/LIST]

By systematically checking these areas, you should be able to identify and resolve the issue causing the 404 errors for your new APIs in Postman.



[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2024-04-26
> **dragonfly41 said:**
> The issue I have is bumping up to v 20.

Errors were encountered while processing:
 /var/cache/apt/archives/nodejs_20.12.2-1nodesource1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I did not have good luck for case use with v 20, will v 22 work for you both?
```
node --version
v22.0.0

```

---

### Post by dragonfly41 on 2024-04-26
If you can provide the link that would be good .. I went to latest node downloads and only Windows showed .. no Linux.

---

### Post by #&amp;thj^% on 2024-04-26
> **dragonfly41 said:**
> If you can provide the link that would be good .. I went to latest node downloads and only Windows showed .. no Linux.

Dang I'll have to find it again It's been a few months since, but for v20 I use:
```
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash - &&\
sudo apt-get install -y nodejs
```
For v22 I use:
```
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash - &&\
sudo apt-get install -y nodejs
```

**I owe the OP an apology for all this noise, but may be useful IJDK.**

Now if you want to remove or revert to the original "v"
```
apt-get purge nodejs &&\
rm -r /etc/apt/sources.list.d/nodesource.list &&\
rm -r /etc/apt/keyrings/nodesource.gpg
```
And I'm a CLI user so I remove the source by:
```
 sudo rm -r '/etc/apt/sources.list.d/nodesource.list' 

```
Update and reinstall the original via:
```
 sudo apt install nodejs
```

EDIT: I found it, I love having good notes: [https://github.com/nodesource/distributions?tab=readme-ov-file#ubuntu-versions](https://github.com/nodesource/distributions?tab=readme-ov-file#ubuntu-versions)

---

### Post by dragonfly41 on 2024-04-26
Good references.

I tried .. 
curl -fsSL [https://deb.nodesource.com/setup_22.x](https://deb.nodesource.com/setup_22.x) | sudo -E bash - &&\sudo apt-get install -y nodejs


reparing to unpack .../nodejs_22.0.0-1nodesource1_amd64.deb ...
Detected old npm client, removing...
Unpacking nodejs (22.0.0-1nodesource1) over (20.12.2-1nodesource1) ...
Setting up nodejs (22.0.0-1nodesource1) ...
Processing triggers for man-db (2.10.2-1) ..

but dang .. node --vesion shows v.18.

I will have to purge node and try again.

Don't know how OP in this buddy thread is faring.

---

### Post by dragonfly41 on 2024-04-26
OP .. I remember using HaXe for the environment you are setting up.

[https://haxe.org/use-cases/desktop/](https://haxe.org/use-cases/desktop/)

[https://community.haxe.org/t/need-some-help-serving-a-nodejs-express-service-over-https/4079/5](https://community.haxe.org/t/need-some-help-serving-a-nodejs-express-service-over-https/4079/5)

[https://haxe.org/documentation/platforms/nodejs.html](https://haxe.org/documentation/platforms/nodejs.html)

---

