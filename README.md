# setup-gitlab-instance-ubuntu
🧪 Install and Configure GitLab instance on Ubuntu 18.04

**Step 1:**

*Installing the dependencies*

`sudo apt update`

`sudo apt install ca-certificates curl openssh-server postfix`

**Step 2:**

*Installing GitLab instance*

`cd /tmp`

`curl -LO https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh`

`sudo apt install gitlab-ce`

**Step 3:**

*Adjusting the firewall rules*

`sudo ufw status`

*Output:*

```bash
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere                  
OpenSSH (v6)               ALLOW       Anywhere (v6)
```

`sudo ufw allow http`

`sudo ufw allow https`

`sudo ufw allow OpenSSH`

`sudo ufw status`

*Output:*

```bash
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere                  
80/tcp                     ALLOW       Anywhere                  
443/tcp                    ALLOW       Anywhere                  
OpenSSH (v6)               ALLOW       Anywhere (v6)             
80/tcp (v6)                ALLOW       Anywhere (v6)             
443/tcp (v6)               ALLOW       Anywhere (v6)
```

**Step 4:**

*Editing the GitLab configuration file*

```bash
sudo nano /etc/gitlab/gitlab.rb
```

**/etc/gitlab/gitlab.rb**

```ruby
##! For more details on configuring external_url see:
##! https://docs.gitlab.com/omnibus/settings/configuration.html#configuring-the-external-url-for-gitlab
external_url 'https://opendevops.dev'
```

```ruby
letsencrypt['contact_emails'] = ['opantazos@gmail.com']
```

```bash
sudo gitlab-ctl reconfigure
```

**Step 5:**

*Launch the GitLab instance*

https://www.opendevops.dev

> READY 
