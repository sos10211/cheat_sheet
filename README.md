# cheat_sheet
cheat sheet for newbies

Git Commands
============
_A list of my commonly used Git commands_


### Getting & Creating Projects

| Command | Description |
| ------- | ----------- |
| `git init`| Initialize a local Git repository |
| `git clone ssh://git@github.com/[username]/[repository-name].git` | Create a local copy of a remote repository |
| `git clone --branch <branchname> <remote-repo-url>` | clone from specific brach |
| `git clone -b <branchname> <remote-repo-url>` |   ''  |

### Basic Snapshotting

| Command | Description |
| ------- | ----------- |
| `git status` | Check status |
| `git add [file-name.txt]` | Add a file to the staging area |
| `git add -A` | Add all new and changed files to the staging area |
| `git commit -m "[commit message]"` | Commit changes |
| `git rm -r [file-name.txt]` | Remove a file (or folder) |

### Branching & Merging

| Command | Description |
| ------- | ----------- |
| `git branch` | List branches (the asterisk denotes the current branch) |
| `git branch -a` | List all branches (local and remote) |
| `git branch [branch name]` | Create a new branch |
| `git branch -d [branch name]` | Delete a branch |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git checkout -b [branch name]` | Create a new branch and switch to it |
| `git checkout -b [branch name] origin/[branch name]` | Clone a remote branch and switch to it |
| `git branch -m [old branch name] [new branch name]` | Rename a local branch |
| `git checkout [branch name]` | Switch to a branch |
| `git checkout -` | Switch to the branch last checked out |
| `git checkout -- [file-name.txt]` | Discard changes to a file |
| `git merge [branch name]` | Merge a branch into the active branch |
| `git merge [source branch] [target branch]` | Merge a branch into a target branch |
| `git stash` | Stash changes in a dirty working directory |
| `git stash clear` | Remove all stashed entries |


### Sharing & Updating Projects

| Command | Description |
| ------- | ----------- |
| `git push origin [branch name]` | Push a branch to your remote repository |
| `git push -u origin [branch name]` | Push changes to remote repository (and remember the branch) |
| `git push` | Push changes to remote repository (remembered branch) |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git pull` | Update local repository to the newest commit |
| `git pull origin [branch name]` | Pull changes from remote repository |
| `git remote add origin ssh://git@github.com/[username]/[repository-name].git` | Add a remote repository |
| `git remote set-url origin ssh://git@github.com/[username]/[repository-name].git` | Set a repository's origin branch to SSH |

### Inspection & Comparison

| Command | Description |
| ------- | ----------- |
| `git log` | View changes |
| `git log --summary` | View changes (detailed) |
| `git log --oneline` | View changes (briefly) |
| `git diff [source branch] [target branch]` | Preview changes before merging |

### Configure .ssh key 

| Command | Description |
| ------- | ----------- |
| `cd ~/.ssh ` | Enter to .ssh dir |
| `ssh-keygen -t rsa -C "your_email@example.com"` | Generate [id_rsa] and [id_rsa.pub] |
#### copy [id_rsa.pub] content and past it on githud [Account > Setting > SSH Keys] then try to [git push] again
***Connect remote host using ssh***
```
ssh [username]@[host_ip_address]
```

### Configure git bash user
| Command | Description |
| ------- | ----------- |
| `git config --list` | Show global config |
| `git config --global user.name "your name"` | Set user name |
| `git config --global user.email "your email"` | Set user email |
| `git config --global user.password "your password"` | Set user password |

### Give permission to usb in linux
`sudo usermod -a -G uucp nanashi`
| -------------------------------- |



### Nginx server ubuntu
#### delete apache server
`systemctl stop apache2`
`systemctl disable apache2`
`apt remove apache2`
#### delete dependemcis
`apt autoremove`

#### Clean and update server
`apt clean all && apt update && apt dist-upgrade`
##### Install nginx
`apt install nginx`
##### Installing and configure Firewall
`apt install ufw`
`ufw enable`
`ufw app list`
`ufw status`
`ufw allow "Nginx Full"`
### Server configuration

#### Create server configuration on `/etc/nginx/sites-available/site_name`

### exmaples:

#### Front-end

```
server {

  root /var/www/your_folde/html;
  index index.html index.htm index.nginx-debian.html;

  server_name domain_name domain_alies;

  location / {
        # for socket.io web socket
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_http_version 1.1;
        # for socket
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
        try_files $uri.html $uri $uri/ /index.html;
  }
}

```

#### Api example

```
server {

  server_name domain_name;

  location / {

        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

        proxy_pass http://localhost:5050;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
  }

}

```

#### link to `/etc/nginx/sites-enabled/*`
`ln -s /etc/nginx/sites-available/example /etc/nginx/sites-enabled/example`

### create static web page on `/var/www/*`
### install git and clone your project
### install node 
### install pm2 for keep runing node server process
`npm install -g pm2`
#### start pm2 instance
`pm2 start --name demo demo.jss -i max`
`pm2 startup ubuntu`


## SSL certificates
`apt install certbot python3-certbot-nginx`
`certbot --nginx -d your_domain.com -d another_domain.com`
#### certificate only vaild for ninty days.To set a timer to validate automatically:
`systemctl status certbot.timer`

#### Linux command
| Command | Description |
| ------------- | ---------------- |
|`sudo apt remove --autoremove <packagename> -y`| delete and clean linux package |
