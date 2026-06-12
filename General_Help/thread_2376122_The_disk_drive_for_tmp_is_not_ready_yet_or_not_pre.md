---
title: "The disk drive for /tmp is not ready yet or not present. Continue to wait ..."
date: 2017-10-30
forum: General Help
---

### Post by blackevanuz on 2017-10-30
Hello 

I updated to 16.04 from 14.04 and now i have this error, i have searched on the internet and for some people doing:

```

sudo mv /tmp /tmp_old
sudo mkdir /tmp
sudo chmod 1777 /tmp
```

Had worked but not for me, i also tried adding 
```

[COLOR=#333333][FONT=monospace]tmpfs /tmp tmpfs defaults 0 0[/FONT][/COLOR]

```

To the end of /etc/fstab but also didnot work,

This is my normal fstab file after i pressed M for manual mount:

[IMG]https://lh3.googleusercontent.com/t9Wtoq-SJZSymE98uXhVh-5rA1gY9Kv8_rs8H2tLLX7X8O57unTC-rmPZ7VMBhLvlGE6WrqdBh5Bpim3xgJt0AjC4idJakGP47V_QoaNkukwpBYTQUlaJcRYlHbVOMy33oUx_tlyRFX_Rd1kj-cqvkMKN3OD5Y6ZM1E0fGgKIyoS0KQGWmopwaJ4_iLqacahiqdJEy1s5xEJfYYN0jlMdIJTYY4jP3jZL2gZBQYqNJBdBYGDDTBf2gk2RnMewB22zUggC4_-qRvGLHZThfCBM2l-XqwWRk6poj8eB27OwUjkAQO8U6LWHY-tG6GAJnfjBUIWFZLdrhQuzaN0S5gnXd4pozlgNI_JlGGAFkPU_vnzT_V_6Ty-XPz9An7l7AM4laByB7lLtNxZTgKLSrv6sx4bpifijJLwfWBkMOaLW2Z2spNoqXqpPO2JZqxlslf5ALDONaVj2HTtypa2UVIelaabKhPmTbS2M1y3OOWn0BSB2DmvrXupS7YqoGelFIF6keE9ScKmwc4qiMtdlF9XRUfHIehXdKl4SjyuaSWW5hNcPhbcbNMCwwOKkem8mX1ANrSbHvyBvVj1P43OW8nF37i3jFdt2XqbrhwIGSu0sh5lngIiKsBzF7ot3C-vJsrI12UHe5JCTpVrk9u7pKLzzkDRFdNqR9IjWTI=w1572-h1178-no[/IMG]


And this is the output blkid

[IMG]https://lh3.googleusercontent.com/t8Q3bHzmbelSnNFJTwPkNApFv6eIePJYyuNogOOWfCDnpQF_-_0-TpK7-f9bqv9jbKgj1JIQrv3kFVhC1i50ok2GNg0K1dLl74C1PY-5Z4asT4hYlvrVqUSgRssTW_QFq2UltOgvcnxfdff-h3nDoDKzE44d-4Qv78n7yifQNLmAtVUoFAlnOwYYXyWifxub3VWrndKAJVHRVdoKXU046-ObYmi_iml-JrAhb5ESwsClQYMU0pMMJDaw0dXrXlRbh_jVltwJ8ZZDeYOPctb2ra7O9q36kSpcP-BoTBuSL0WZO3gsyUH337dPREIFI8SwrVxP623HJ-xATdlkJ2T53Bw_ZOveMvM-rPWB7btdnb-Av9UDNALM6T9BzvFhL3sHYQY3DKZU5a6bE6Xkb4Smgba-9I3Jda-Yy3jATDsQxHRO8bsMf7Du_JQugvwvLiSNmOTzgpzMJDVlfcoxPiCJPZm8QtKPRD46hW2CZ5H7W-E53K7qR90OAhuez5ArQN4IyNV9R43ZEgZMJ2JUN_zKq7qhDAxCv-uEtow4LP7pcCcx7y6Gc55j9G03My7MvGldmrVGTe6hp281R_UoTbDVXGl9s9VII5FQh0YnUSgdp1yKd2kyMziopSfWIzxZtGgAX_1oXKALb1BEkpFuJxFafOXMNan_zvnDepI=w1572-h1178-no[/IMG]

---

### Post by blackevanuz on 2017-10-31
Any recommendations?

Thanks!

---

