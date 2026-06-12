---
title: "ISC Kea 1.4.0-P1 on Ubuntu 18.10"
date: 2019-01-23
forum: General Help
---

### Post by coctien12 on 2019-01-23
[COLOR=#000000]Hi,[/COLOR]

[COLOR=#000000]I have two Raspberry PIs running Ubuntu 18.10 with ISC Kea 1.4.0-PI installed from the Ubuntu repository. [/COLOR]
[COLOR=#000000]I am trying to run Kea in High Availability mode but the control commands can not be executed as the control-agent-commands.so hook is missing and the control sockets are not being created.
```

[/COLOR]// This is a basic configuration for the Kea Control Agent.
//
// This is just a very basic configuration. Kea comes with large suite (over 30)
// of configuration examples and extensive Kea User's Guide. Please refer to
// those materials to get better understanding of what this software is able to
// do. Comments in this configuration file sometimes refer to sections for more
// details. These are section numbers in Kea User's Guide. The version matching
// your software should come with your Kea package, but it is also available
// on Kea web page (http://kea.isc.org, click User's Guide, direct link for
// stable version is http://kea.isc.org/docs/kea-guide.html).
//
// This configuration file contains only Control Agent's configuration.
// If configurations for other Kea services are also included in this file they
// are ignored by the Control Agent.
{

// This is a basic configuration for the Kea Control Agent.
// RESTful interface to be available at http://127.0.0.1:8080/
"Control-agent": {
    "http-host": "172.16.26.249",
    "http-port": 8080,

    // Specify location of the files to which the Control Agent
    // should connect to forward commands to the DHCPv4 and DHCPv6
    // server via unix domain socket.
    "control-sockets": {
        "dhcp4": {
            "socket-type": "unix",
            "socket-name": "/tmp/kea-dhcp4-ctrl.sock"
        },
        "dhcp6": {
            "socket-type": "unix",
            "socket-name": "/tmp/kea-dhcp4-ctrl.sock"
        }
    },
    

    // Specify hooks libraries that are attached to the Control Agent.
    // Such hooks libraries should support 'control_command_receive'
    // hook point. This is currently commented out because it has to
    // point to the existing hooks library. Otherwise the Control
    // Agent will fail to start.
    "hooks-libraries": [
      {
       "library": "/usr/lib/arm-linux-gnueabihf/hooks/control-agent-commands.so",
       "parameters": {
           "param1": "foo"
         }
      },
      {
        "library": "/usr/lib/arm-linux-gnueabihf/hooks/libdhcp_ha.so",
        "parameters" : {
                         "high-availability": [ {
                               "this-server-name": "pi-one",
                               "mode": "load-balancing",
                               "send-leases-updates": true,
                               "sync-leases": true,
                               "heartbeat-delay": 10000,
                               "max-response-delay": 10000,
                               "max-ack-delay": 5000,
                               "max-unacked-clients": 10,
                               "peers": [
                                   {
                                       "name": "pi-one",
                                       "url": "http://172.16.26.249:8080/",
                                       "role": "primary", 
                                       "auto-failover": true
                                   },
                                   {
                                       "name": "pi-two",
                                       "url": "http://172.16.26.247:8080/",
                                       "role": "secondary",
                                       "auto-failover": true
                                   }
                               ]
                           } ]
                       }
      }
    ]
},

// Logging configuration starts here. Kea uses different loggers to log various
// activities. For details (e.g. names of loggers), see Chapter 18.
"Logging":
{
  "loggers": [
    {
        // This specifies the logging for Control Agent daemon.
        "name": "kea-ctrl-agent",
        "output_options": [
            {
                // Specifies the output file. There are several special values
                // supported:
                // - stdout (prints on standard output)
                // - stderr (prints on standard error)
                // - syslog (logs to syslog)
                // - syslog:name (logs to syslog using specified name)
                // Any other value is considered a name of a time
                "output": "/var/log/kea/kea-ctrl-agent.log"

                // This governs whether the log output is flushed to disk after
                // every write.
                // "flush": false,

                // This specifies the maximum size of the file before it is
                // rotated.
                // "maxsize": 1048576,

                // This specifies the maximum number of rotated files to keep.
                // "maxver": 8
            }
        ],
        // This specifies the severity of log messages to keep. Supported values
        // are: FATAL, ERROR, WARN, INFO, DEBUG
        "severity": "INFO",

        // If DEBUG level is specified, this value is used. 0 is least verbose,
        // 99 is most verbose. Be cautious, Kea can generate lots and lots
        // of logs if told to do so.
        "debuglevel": 0
    }
  ]
}
}[COLOR=#000000]
```
[/COLOR][COLOR=#000000]Is there a work around for this ?[/COLOR]

---

