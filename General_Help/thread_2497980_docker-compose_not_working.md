---
title: "docker-compose not working"
date: 2024-05-24
forum: General Help
---

### Post by kingpenguin on 2024-05-24
I have docker-compose 1.29.2 and docker 24.0.7 but when I try to run docker compose on a compose file I get the following error.

[HTML]Traceback (most recent call last):  File "/usr/lib/python3/dist-packages/docker/api/client.py", line 214, in _retrieve_server_version    return self.version(api_version=False)["ApiVersion"]           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^  File "/usr/lib/python3/dist-packages/docker/api/daemon.py", line 181, in version    return self._result(self._get(url), json=True)                        ^^^^^^^^^^^^^^  File "/usr/lib/python3/dist-packages/docker/utils/decorators.py", line 46, in inner    return f(self, *args, **kwargs)           ^^^^^^^^^^^^^^^^^^^^^^^^  File "/usr/lib/python3/dist-packages/docker/api/client.py", line 237, in _get    return self.get(url, **self._set_request_timeout(kwargs))           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^  File "/usr/lib/python3/dist-packages/requests/sessions.py", line 602, in get    return self.request("GET", url, **kwargs)           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^  File "/usr/lib/python3/dist-packages/requests/sessions.py", line 589, in request    resp = self.send(prep, **send_kwargs)           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^  File "/usr/lib/python3/dist-packages/requests/sessions.py", line 703, in send    r = adapter.send(request, **kwargs)        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^  File "/usr/lib/python3/dist-packages/requests/adapters.py", line 486, in send    resp = conn.urlopen(           ^^^^^^^^^^^^^  File "/usr/lib/python3/dist-packages/urllib3/connectionpool.py", line 791, in urlopen    response = self._make_request(               ^^^^^^^^^^^^^^^^^^^  File "/usr/lib/python3/dist-packages/urllib3/connectionpool.py", line 497, in _make_request    conn.request(TypeError: HTTPConnection.request() got an unexpected keyword argument 'chunked'
During handling of the above exception, another exception occurred:
Traceback (most recent call last):  File "/usr/bin/docker-compose", line 33, in <module>    sys.exit(load_entry_point('docker-compose==1.29.2', 'console_scripts', 'docker-compose')())             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^  File "/usr/lib/python3/dist-packages/compose/cli/main.py", line 81, in main    command_func()  File "/usr/lib/python3/dist-packages/compose/cli/main.py", line 200, in perform_command    project = project_from_options('.', options)              ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^  File "/usr/lib/python3/dist-packages/compose/cli/command.py", line 60, in project_from_options    return get_project(           ^^^^^^^^^^^^  File "/usr/lib/python3/dist-packages/compose/cli/command.py", line 152, in get_project    client = get_client(             ^^^^^^^^^^^  File "/usr/lib/python3/dist-packages/compose/cli/docker_client.py", line 41, in get_client    client = docker_client(             ^^^^^^^^^^^^^^  File "/usr/lib/python3/dist-packages/compose/cli/docker_client.py", line 170, in docker_client    client = APIClient(use_ssh_client=not use_paramiko_ssh, **kwargs)             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^  File "/usr/lib/python3/dist-packages/docker/api/client.py", line 197, in __init__    self._version = self._retrieve_server_version()                    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^  File "/usr/lib/python3/dist-packages/docker/api/client.py", line 221, in _retrieve_server_version    raise DockerException(docker.errors.DockerException: Error while fetching server API version: HTTPConnection.request() got an unexpected keyword argument 'chunked[/HTML]

If anyone has some idea how to fix this I would be very grateful

---

### Post by kingpenguin on 2024-05-24
I also wanted to add that I am not using any 3rd party repos that have docker in them. The only ones I have is google chrome and nordvpn.  I am on ubuntu 24.04

---

### Post by eindgebruiker on 2024-05-27
[https://bugs.launchpad.net/ubuntu/+source/docker-compose/+bug/2056735](https://bugs.launchpad.net/ubuntu/+source/docker-compose/+bug/2056735)

---

