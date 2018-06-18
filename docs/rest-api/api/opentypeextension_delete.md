# Delete open extension

Delete an open extension ([openTypeExtension](../resources/openTypeExtension.md) object) from the specified instance of a resource. 

## Permissions

One of the following permissions is required to call this API, depending on the resource you're deleting the extension from. To learn more, including how to choose permissions, see [Permissions](../concepts/permissions_reference.md).

|**Supported resource**|**Permission**|**Supported resource**|**Permission** |
|:-----|:-----|:-----|:-----|
| [device](../resources/device.md) | Device.ReadWrite.All | [event](../resources/event.md) | Calendars.ReadWrite |
| [group](../resources/group.md) | Group.ReadWrite.All | [group event](../resources/event.md) | Group.ReadWrite.All |
| [group post](../resources/post.md) | Group.ReadWrite.All | [message](../resources/message.md) | Mail.ReadWrite |
| [organization](../resources/organization.md) | Directory.AccessAsUser.All | [personal contact](../resources/contact.md) | Contacts.ReadWrite |
| [user](../resources/user.md) | Directory.AccessAsUser.All | | |

## HTTP request
In the request, identify the resource instance, use the **extensions** 
navigation property of that instance to identify the extension, and do a `DELETE` on that extension instance.

<!-- { "blockType": "ignored" } -->
```http
DELETE /devices/{Id}/extensions/{extensionId}
DELETE /users/{id|userPrincipalName}/events/{id}/extensions/{extensionId}
DELETE /groups/{id}/extensions/{extensionId}
DELETE /groups/{id}/events/{id}/extensions/{extensionId}
DELETE /groups/{id}/threads/{id}/posts/{id}/extensions/{extensionId}
DELETE /users/{id|userPrincipalName}/messages/{id}/extensions/{extensionId}
DELETE /organization/{Id}/extensions/{extensionId}
DELETE /users/{id|userPrincipalName}/contacts/{id}/extensions/{extensionId}
DELETE /users/{id|userPrincipalName}/extensions/{extensionId}
```

>**Note:** The above syntax shows some common ways to identify a resource instance, in order to delete an extension from it. 
All other syntax that allows you to identify these resource instances supports deleting open extensions from them in a similar way.

## Path parameters
|Parameter|Type|Description|
|:-----|:-----|:-----|
|id|string|A unique identifier for an instance in the corresponding collection. Required.|
|extensionId|string|This can be an extension name which is a unique text identifier for the extension, or a fully qualified name which concatenates the extension type and unique text identifier. The fully qualified name is returned in the `id` property when you create the extension. Required.|

## Request headers
| Name       | Value |
|:---------------|:----------|
| Authorization | Bearer {token}. Required. |

## Request body
Do not supply a request body for this method.

## Response

If successful, this method returns `204 No Content` response code. It does not return anything in the response body.

## Example
##### Request
The first example references an extension by its name and deletes the extension in the specified message.
<!-- {
  "blockType": "request",
  "sampleKeys": ["Com.Contoso.Referral"],
  "name": "delete_opentypeextension"
}-->
```http
DELETE https://graph.microsoft.com/v1.0/me/messages/{message-id}/extensions/Com.Contoso.Referral
```

The second example deletes an extension in the specified group event.

<!-- { "blockType": "ignored" } -->
```http
DELETE https://graph.microsoft.com/v1.0/groups/{group-id}/events/{event-id}/extensions/Com.Contoso.Referral
```

 

##### Response
Here is an example of the response.
<!-- {
  "blockType": "response",
  "truncated": false
} -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Delete opentypeextension",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->