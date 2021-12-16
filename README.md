## 1 Creando Proyecto

```bash
ng new FRONT-Angular-api
```

Nos preguntará agregar routing y le damos a que si

```bash
Would you like to add Angular routing? (y/N) yes
```

Luego nos pregunta sobre si usar CSS solo u otros frameworks, escojeremos css y al dar ENTER empezará a crear neustro nuevo proyecto.

| Ingresamos al proyecto para probar el servidor:

```bash
ng serve 
```

### 1.2 Run Server
```bash
ng serve --host=0.0.0.0 --disable-host-check 
```

```bash
ng serve --sourceMap=false --host=0.0.0.0 --disable-host-check 
```


## 2 Creando Componentes

```bash
ng g component component/navbar
```

```bash
ng g component component/user-add
```

```bash
ng g component component/user-list
```

Y dentro de nuestro **src/app/component** tendremos creado nuestros nuevos componentes:
![](ANEXOS/Pasted%20image%2020211119190641.png)

Ahora crearemos **servicios** y **modelos**:

## 3 Creando MODELOS y SERVICIOS
### 3.1 Modelos
Los modelos nos serviran para tener la estructura de nuestro modelo:

```bash
ng g class model/user
```

### 3.2 Servicios
Esta contine los metodos para hacer /GET /POST /PUT /DELETE

```bash
ng g service service/user
```

--------- 

## 4 REGISTRAMOS LIBRERIAS
Vamos a registrar las librerias que usaremos en **app.module.ts**
```javascript
HttpClientModule,
FormsModule
```

Debe quedar asi:
![](ANEXOS/Pasted%20image%2020211119195830.png)
Ahora importamos para borrar esos errores, importaremos lo que falta:

```js
import { FormsModule } from '@angular/forms';
import { HttpClientModule } from '@angular/common/http'
```
![](ANEXOS/Pasted%20image%2020211119200354.png)
| DEF:
**FormsModule:** Sirve para recoger los datos de los formularios.
**HttpClientModule:** Este nos sirve para hacer  losservicios /GET /POST /PUT /DELETE 

----------

## 5 Configurando el **MODELO**
Nos vamos a **src/app/model/user.ts**
![](ANEXOS/Pasted%20image%2020211119201425.png)
y agregamos esto:

```js
export class User {
    id?:number | null;
    nombres?:string;
    apellidos?:string;
    razonsocial?:string;
    direccion?:string;
    ruc?:string;
    celular?:string;
}
```
Deberia quedar asi igual al modelo de nuestro backend:
![](ANEXOS/Pasted%20image%2020211119202911.png)

## 6 COMPONENTE NAV HTML
Agregando este codigo a **src/app/components/navbar/navbar.component.html**

```html
<nav class="navbar navbar-expand-lg fixed-top navbar-dark bg-dark" aria-label="Main navigation">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Offcanvas navbar</a>
    <button class="navbar-toggler p-0 border-0" type="button" id="navbarSideCollapse" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="navbar-collapse offcanvas-collapse" id="navbarsExampleDefault">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <a class="nav-link active" aria-current="page" href="#">Dashboard</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Notifications</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Profile</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Switch account</a>
        </li>
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" id="dropdown01" data-bs-toggle="dropdown" aria-expanded="false">Settings</a>
          <ul class="dropdown-menu" aria-labelledby="dropdown01">
            <li><a class="dropdown-item" href="#">Action</a></li>
            <li><a class="dropdown-item" href="#">Another action</a></li>
            <li><a class="dropdown-item" href="#">Something else here</a></li>
          </ul>
        </li>
      </ul>
      <form class="d-flex">
        <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
        <button class="btn btn-outline-success" type="submit">Search</button>
      </form>
    </div>
  </div>
</nav>
```

## 7 Agregando BOOTSTRAP - CSS FrameWorks
Nos dirigimos a **src/index.html** y agregamos esto arriba de ``<head>``:

```html
<!-- Font Awesome -->
<link
  href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.1/css/all.min.css"
  rel="stylesheet"
/>
<!-- Google Fonts -->
<link
  href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap"
  rel="stylesheet"
/>
<!-- MDB -->
<link
  href="https://cdnjs.cloudflare.com/ajax/libs/mdb-ui-kit/3.10.0/mdb.min.css"
  rel="stylesheet"
/>
```

Y el JS al finalizar el body osea encima de ``</body>``:

```html
<!-- MDB -->
<script
  type="text/javascript"
  src="https://cdnjs.cloudflare.com/ajax/libs/mdb-ui-kit/3.10.0/mdb.min.js"
></script>
```


##  INFO **``<app-root>``**
|  ``<app-root></app-root>`` esta hubicado en ** src/app/** y sus archivos son **app.component.html** y **app.component.html** como lo indica su codigo, entonces ese es el html que se esta mostrando en nuestro **home**:

![](ANEXOS/Pasted%20image%2020211119205713.png)

## 8 Insert component in HOME

Nos vamos a **src/app/app.component.html** y eliminamos todo el codigo excepto 

```html
<router-outlet></router-outlet>
```

y solo deberiamos tener eso y agregamos nuestro **nav-bar**:

```html
<app-navbar></app-navbar>

<router-outlet></router-outlet>
```

Colocaremos nuestro **nav-bar component** en la home:

```html
<app-navbar></app-navbar>
<div class="container">
  <router-outlet></router-outlet>
</div>
```

### RUN SERVE

```bash
ng serve --host=0.0.0.0 --disable-host-check 
```

```bash
ng serve --sourceMap=false --host=0.0.0.0 --disable-host-check 
```


## 9 ROUTING Enrutamiento
Nos dirigimos a **src/app/app-routing.module.ts** y dentro de ``const routes`` jalamos las rutas de LISTAR y AGREGAR.
![](ANEXOS/Pasted%20image%2020211120075154.png)



```js
{path:"usuarios",component:UserListComponent}
```
![](ANEXOS/app-routing.module.ts%20-%20FRONT-Angular-api%20-%20Visual%20Studio%20Code.jpg)

y para poder acceder a esta ruta usaremos este codigo en html:

```html
 <li class="nav-item">
 <a class="nav-link active" href="#" routerLink="usuarios">Usuarios</a>
 </li>
```

``routerLink="usuarios"`` nos ayuda a acceder rapidamente sin cargar la pagina frente a ``href`` .

## 10 Creando TABLA para Listar USUARIOS
 En el componente **src\app\component\user-list\user-list.component.html**
```html
<table class="table">
    <thead class="table-dark">
      <tr>
        <th scope="col">#</th>
        <th scope="col">Nombres</th>
        <th scope="col">Apellidos</th>
        <th scope="col">Razon Social</th>
        <th scope="col">Dirección</th>
        <th scope="col">Ruc</th>
        <th scope="col">Celular</th>
        <th scope="col">Opciones</th>
      </tr>
    </thead>
    <tbody>
      <tr *ngFor="let item of listaUsuarios">
        <th scope="row">{{ item.id }}</th>
        <td>{{ item.nombres }}</td>
        <td>{{ item.apellidos }}</td>
        <td>{{ item.razonsocial }}</td>
        <td>{{ item.direccion }}</td>
        <td>{{ item.ruc }}</td>
        <td>{{ item.celular }}</td>
        <td>
            <a href="#" >Editar</a> | <a href="#" >Eliminar</a> 
        </td>
      </tr>
    </tbody>
  </table>
```
En **src\app\component\user-list\user-list.component.ts** Deberia quedarnos asi:

```js
import { Component, OnInit } from '@angular/core';
import { UserService } from 'src/app/service/user.service';

@Component({
  selector: 'app-user-list',
  templateUrl: './user-list.component.html',
  styleUrls: ['./user-list.component.css']
})
export class UserListComponent implements OnInit {

  listaUsuarios:any;
  constructor(private userService:UserService) { }

  ngOnInit(): void {
    this.userService.getUsers().subscribe((usuarios:any) => {
      this.listaUsuarios=usuarios;
    })
    
  }

}
```


## 11 Formulario Para Añadir USUARIOS








-----------------------


## Creando Nuevo Componente y Enrutarlo

Hubicamos nuestro component.ts de nuestro componente y copiamos este identificador:
![](ANEXOS/Pasted%20image%2020211123235345.png)

Luego nos vamos a **src\app\app-routing.module.ts** y agregamos dos nuevas lienas una para importar nuestro componente y el otro para darle una ruta.

![](ANEXOS/Pasted%20image%2020211123235537.png)
Al darle una ruta en este ejemplo de la imagen es `'datos'` esta misma la usaremos en nuestro codigo html para invocarla ejemplo.

```html
 <li class="nav-item">
 <a class="nav-link" href="" routerLink="datos">form1</a>
 </li>
 ```
 
