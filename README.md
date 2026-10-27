# linux-world

Hands-on Linux playground: a home storage server (serverlin) rebuilt from code with Ansible.

## Rebuilding serverlin

1. Install Ubuntu Server 26.04 LTS by hand, create user `serverux`, enable OpenSSH.
2. Install git and Ansible (same way as on the original server).
3. Clone this repo: `git clone https://github.com/rmsaran/linux-world.git`
4. Run everything:
   `cd linux-world/ansible && sudo ansible-playbook -i localhost, site.yml -e ansible_python_interpreter=/usr/bin/python3`
5. Manual steps Ansible does not do (secrets):
   - `sudo tailscale up` and sign in
   - `sudo smbpasswd -a serverux`
6. Restore data from backup (shares, `/var/lib/filebrowser/filebrowser.db`).
7. Filebrowser is hand-built: v2.63.23 binary in `/usr/local/bin`, service file, port 8080, root `/home/serverux/shares/StorageServer`. The project is archived.

Playbooks: quiet-console, cockpit, samba, tailscale, firewall (run in that order by `site.yml`).
