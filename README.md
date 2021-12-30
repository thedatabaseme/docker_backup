Docker_Backup
=========

This Playbook enables Backups all persistent Volumes (no Bind Mounts) from a given List of Containers to a Folder of your choice. The Volume Data will be backed up as a compressed tar.

Requirements
------------

- Ansible 2.10

Playbook Variables
--------------

- `backup_location` (Default `/docker/backup`): Defines the Backup Location of the Volumes.
- `container_list_to_backup`: A Dictionary of Containers you want to backup. (Must be the same Name than in Docker). 

  Example Container List:

      container_list_to_backup:
      - container_name: myShinyContainer1
      - container_name: myShinyContainer2

- `delete_old_backups` (Default `true`): Controls if you want to delete old backups or not
- `backup_retention`: Number of days for backups you want to get preserved. Older Backups will get deleted

Example Playbook run Command
----------------

An example Playbook Call looks like this. Ofcourse you may want to specify the Variables within your Playbook or within your Inventory:

    - ansible-playbook -i hosts -e "HOSTS=myDockerHost" docker_backup.yml

Maybe you want to specify the Container Dictionary in a separate File. Then you can call the Playbook like so:

    - ansible-playbook -i hosts -e "@container_list_to_backup.yml" -e "HOSTS=myDockerHost" docker_backup.yml

Author Information
------------------

This Role is created by P. Haberkern (thedatabaseme)
