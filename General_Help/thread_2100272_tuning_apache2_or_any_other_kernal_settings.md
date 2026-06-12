---
title: "tuning apache2 or any other kernal settings"
date: 2013-01-01
forum: General Help
---

### Post by sayalik6 on 2013-01-01
Hi guys,

Our website is hosted on ubuntu machine. We are testing connection pooling with the help of Jmeter. If we test with 500 hits, only 150-160 users are getting connected and for others we are getting following error.

 [COLOR=Navy]org.apache.http.conn.
HttpHostConnectException: Connection to [http://XXX.com](http://XXX.com) refused
    at org.apache.http.impl.conn.DefaultClientConnectionOperator.openConnection(DefaultClientConnectionOperator.java:190)
    at org.apache.http.impl.conn.ManagedClientConnectionImpl.open(ManagedClientConnectionImpl.java:294)
    at org.apache.http.impl.client.DefaultRequestDirector.tryConnect(DefaultRequestDirector.java:640)
    at org.apache.http.impl.client.DefaultRequestDirector.execute(DefaultRequestDirector.java:479)
    at org.apache.http.impl.client.AbstractHttpClient.execute(AbstractHttpClient.java:906)
    at org.apache.http.impl.client.AbstractHttpClient.execute(AbstractHttpClient.java:805)
    at org.apache.jmeter.protocol.http.sampler.HTTPHC4Impl.sample(HTTPHC4Impl.java:284)
    at org.apache.jmeter.protocol.http.sampler.HTTPSamplerProxy.sample(HTTPSamplerProxy.java:62)
    at org.apache.jmeter.protocol.http.sampler.HTTPSamplerBase.sample(HTTPSamplerBase.java:1075)
    at org.apache.jmeter.protocol.http.sampler.HTTPSamplerBase.sample(HTTPSamplerBase.java:1064)
    at org.apache.jmeter.threads.JMeterThread.process_sampler(JMeterThread.java:426)
    at org.apache.jmeter.threads.JMeterThread.run(JMeterThread.java:255)
    at java.lang.Thread.run(Unknown Source)
Caused by: java.net.ConnectException: Connection timed out: connect
    at java.net.PlainSocketImpl.socketConnect(Native Method)
    at java.net.PlainSocketImpl.doConnect(Unknown Source)
    at java.net.PlainSocketImpl.connectToAddress(Unknown Source)
    at java.net.PlainSocketImpl.connect(Unknown Source)
    at java.net.SocksSocketImpl.connect(Unknown Source)
    at java.net.Socket.connect(Unknown Source)
    at org.apache.http.conn.scheme.PlainSocketFactory.connectSocket(PlainSocketFactory.java:127)
    at org.apache.http.impl.conn.DefaultClientConnectionOperator.openConnection(DefaultClientConnectionOperator.java:180)
    ... 12 more
[/COLOR] 
We tried to tune up apache config, tomcat config files and some of the kernal variables too...but nothing is working.....anyone can help???

---

