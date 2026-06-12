---
title: "npm install failure on 18.04"
date: 2022-06-10
forum: General Help
---

### Post by allsolution on 2022-06-10
I have installed nodejs 12 on ubuntu 18.04 succesfully.
But I am trying npm installing it get's that error.
What config I missed? I uninsalled 12 and installed 16 but error goes stay same.
```


root@ubuntu:/etc/apt/sources.list.d# nodejs -v
v12.22.12
root@ubuntu:/etc/apt/sources.list.d# npm -v
6.14.16
root@ubuntu:/etc/apt/sources.list.d# cd /
root@ubuntu:/# cd /var/www/mysite
root@ubuntu:/var/www/mysite# npm install


> ngrok@4.3.1 postinstall /var/www/mysite/node_modules/ngrok
> node ./postinstall.js


ngrok - downloading binary https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip
ngrok - downloading progress: ngrok - error storing binary to local file [Error: EACCES: permission denied, open '/var/www/mysite/node_modules/ngrok/bin/aHR0cHM6Ly9iaW4uZXF1aW5veC5pby9jLzRWbUR6QTdpYUhiL25ncm9rLXN0YWJsZS1saW51eC1hbWQ2NC56aXA=.zip'] {
  errno: -13,
  code: 'EACCES',
  syscall: 'open',
  path: '/var/www/mysite/node_modules/ngrok/bin/aHR0cHM6Ly9iaW4uZXF1aW5veC5pby9jLzRWbUR6QTdpYUhiL25ncm9rLXN0YWJsZS1saW51eC1hbWQ2NC56aXA=.zip'
}
ngrok - install failed, retrying
ngrok - downloading binary https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip
ngrok - downloading progress: ngrok - error storing binary to local file [Error: EACCES: permission denied, open '/var/www/mysite/node_modules/ngrok/bin/aHR0cHM6Ly9iaW4uZXF1aW5veC5pby9jLzRWbUR6QTdpYUhiL25ncm9rLXN0YWJsZS1saW51eC1hbWQ2NC56aXA=.zip'] {
  errno: -13,
  code: 'EACCES',
  syscall: 'open',
  path: '/var/www/mysite/node_modules/ngrok/bin/aHR0cHM6Ly9iaW4uZXF1aW5veC5pby9jLzRWbUR6QTdpYUhiL25ncm9rLXN0YWJsZS1saW51eC1hbWQ2NC56aXA=.zip'
}
ngrok - install failed, retrying
ngrok - downloading binary https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip
ngrok - downloading progress: ngrok - error storing binary to local file [Error: EACCES: permission denied, open '/var/www/mysite/node_modules/ngrok/bin/aHR0cHM6Ly9iaW4uZXF1aW5veC5pby9jLzRWbUR6QTdpYUhiL25ncm9rLXN0YWJsZS1saW51eC1hbWQ2NC56aXA=.zip'] {
  errno: -13,
  code: 'EACCES',
  syscall: 'open',
  path: '/var/www/mysite/node_modules/ngrok/bin/aHR0cHM6Ly9iaW4uZXF1aW5veC5pby9jLzRWbUR6QTdpYUhiL25ncm9rLXN0YWJsZS1saW51eC1hbWQ2NC56aXA=.zip'
}
ngrok - install failed [Error: EACCES: permission denied, open '/var/www/mysite/node_modules/ngrok/bin/aHR0cHM6Ly9iaW4uZXF1aW5veC5pby9jLzRWbUR6QTdpYUhiL25ncm9rLXN0YWJsZS1saW51eC1hbWQ2NC56aXA=.zip'] {
  errno: -13,
  code: 'EACCES',
  syscall: 'open',
  path: '/var/www/mysite/node_modules/ngrok/bin/aHR0cHM6Ly9iaW4uZXF1aW5veC5pby9jLzRWbUR6QTdpYUhiL25ncm9rLXN0YWJsZS1saW51eC1hbWQ2NC56aXA=.zip'
}
npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! ngrok@4.3.1 postinstall: `node ./postinstall.js`
npm ERR! Exit status 1
npm ERR!
npm ERR! Failed at the ngrok@4.3.1 postinstall script.
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.



```

---

### Post by Xian on 2022-06-12
This might be of some help: 

[https://github.com/inconshreveable/ngrok/issues/429#issuecomment-458989223](https://github.com/inconshreveable/ngrok/issues/429#issuecomment-458989223)

---

