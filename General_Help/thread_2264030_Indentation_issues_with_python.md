---
title: "Indentation issues with python"
date: 2015-02-04
forum: General Help
---

### Post by syedk on 2015-02-04
I downlooaded this code and am attempting to run it. I keep getting indentation error. I realize this is an Ubuntu forum but perhaops there is a way to handle it with a editor which can nrecognize the tab or space issue.

I have encased the error mesage with line 23 between "****************"
```

import sys
import azure
import socket
 
from azure.servicebus import (
_service_bus_error_handler
)
 
from azure.servicebus.servicebusservice import (
ServiceBusService,
ServiceBusSASAuthentication
)
 
from azure.http import (
HTTPRequest,
HTTPError
)
 
from azure.http.httpclient import _HTTPClient
 
class EventHubClient(object):
def sendMessage(self,body,partition):eventHubHost =
"pac-ns.servicebus.windows.net"
    httpclient = _HTTPClient(service_instance=self)
 ********************************************************************def sendMessage(self,body,partition):
      ^
IndentationError: expected an indented block

***********************************************************************
sasKeyName = "SendPolicy"
sasKeyValue = "erENqf/5wdWCNEbCA9NsDIRqd5MRKdkii07+wezl/NU="
 
authentication = ServiceBusSASAuthentication(sasKeyName,sasKeyValue)
 
request = HTTPRequest()
request.method = "POST"
request.host = eventHubHost
request.protocol_override = "https"
request.path = "/myhub/publishers/" + partition + "/messages?api-version=2014-05
"
request.body = body
request.headers.append(('Content-Type', 'application/atom+xml;type=entry;charset
=utf-8'))
 
authentication.sign_request(request, httpclient)
 
request.headers.append(('Content-Length', str(len(request.body)))
```

---

### Post by Peptid on 2015-02-05
Hi,

I generally use VIM as an editor. You can try to copy-paste the same code into a file with .py extension and try to open it with VIM. I tried now, though it is still not working, it seems that these errors are manageable.

So, in short, my advice is to use VIM. You can also try to take a look at [https://github.com/mbrochh/vim-as-a-python-ide](https://github.com/mbrochh/vim-as-a-python-ide) Maybe this will help you for a long term solution.

Hope this helps.

---

### Post by schragge on 2015-02-05
Just a wild guess:
```

class EventHubClient(object):
    def sendMessage(self,body,partition):
        eventHubHost = "pac-ns.servicebus.windows.net"
        httpclient = _HTTPClient(service_instance=self)
        sasKeyName = "SendPolicy"
        sasKeyValue = "erENqf/5wdWCNEbCA9NsDIRqd5MRKdkii07+wezl/NU="


        authentication = ServiceBusSASAuthentication(sasKeyName,sasKeyValue)


        request = HTTPRequest()
        request.method = "POST"
        request.host = eventHubHost
        request.protocol_override = "https"
        request.path = "/myhub/publishers/" + partition + "/messages?api-version=2014-05"
        request.body = body
        request.headers.append(('Content-Type', 'application/atom+xml;type=entry;charset=utf-8'))


        authentication.sign_request(request, httpclient)


        request.headers.append(('Content-Length', str(len(request.body)))

```
But actually, you should follow the advice you've got on the python list, and download the code in such a way that will preserve its identation.

---

