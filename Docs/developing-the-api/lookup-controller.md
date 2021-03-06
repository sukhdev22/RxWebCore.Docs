---
title: LookupController
author: rxcontributorone
category: developing-the-api
---

Large modules have entities which need to be bind as a dropdown, In such cases a lookup controller is made for the module which accesses Uow to manipulate data based upon the entity and display the data of module entities in a dropdown.  

The controller must be inherited from the class `BaseLookupController`. The controller will have a predefined route which include the controller name. For example: `[Route("api/CountryLookupsController")]` 

# Generate a Lookup Controller

To create a lookup controller, open the `Package Manager Console` and run the following command.

> rxwebcore --controller --lookup --main <Controller_Name> --uow <Module_Name>

Lets consider a scenario where you want to create a `CountryLookupsController` in the `UsersModule`, you have to write:

> rxwebcore --controller --lookup --main CountryLookups --uow User

`CountryLookups` is the controller name and `User` is the module name. It will create a controller `CountryLookupsController` in lookup folder of api in the project

# Add lookups 
Adding lookups in the controller:

> rxwebcore --controller --lookup --main <Country_Name> --uow <Module_Name> --add-lookups <Lookup>

As per this controller : 

> rxwebcore --controller --lookup --main CountryLookups --uow CountryLookup --add-lookups vCountryLookups

# Methods

<table class="table table-bordered">
<tr><th>Method</th><th>Return Type</th><th>Request Params</th><th>Request Body</th><th>Response</th></tr>
<tr><td>AllAsync</td><td>list</td><td> - </td><td> - </td><td>complete list of that entity</td></tr>
<tr><td>OrderBy</td><td>list</td><td>predicate</td><td> - </td><td>list</td></tr>
<tr><td>Where</td><td>list</td><td>predicate</td><td> - </td><td>list</td></tr>
</table>

# Example

```js
    [ApiController]
    [Route("api/[controller]")]
	
	public class ResourceLookUpsController : BaseLookupController
    {
        public ResourceLookUpsController(IResourceLookUpUow uow):base(uow) {}

        #region Lookups
        #endregion Lookups
    }
}

```