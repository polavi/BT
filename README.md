# BT
ReParenting Web Service

Post operation requires a Name, and a BT Id.

If An Account is not found to match the BT Id, or The Name, a new Account will be created by that Name and BT Id.

If an existing account matches the BT Id, Then a search is made for an account matching the name, an not having a prent; 
if found, it is set as the parent of the account referenced by BT Id in web service call.

If a match is found for Name (but not BT Id), then a new acount is created with web service values of name, and BT Id, and the 
account that matched the name is set as the parent.

To Test:

(1) Initiate a Post service call with name, and BT Id's that the have no corresponding existing account in Salesforce instance.
  This should result in a new Account(name, BT Id) to be created with no parent Id.
  
(2) Initiate a post service call with a name, and BT Id for which an account already exists, but non other that matches the name.
  This should not result in a new Account or any changes to the existing matching account.
  
(3) Initiate a post service call with a name, and BT Id for which an account already exists, with other account(s) matching the name.
  This should not result in parent Account being set to the account matching the name, not matching the BT Id, and not having a parent.
  
(4) Initiate a post service call with a name, and BT Id where:
    No Existing account matches both name, and BT Id
    Existing Account does match the Name
    This should result in the creation of a new Account(name, BT Id), with parent Id set to existing Account with matching name.
